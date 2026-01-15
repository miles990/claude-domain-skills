# 量化交易程式碼範例

> 本文件包含量化交易 skill 的完整程式碼範例

## 技術指標工具箱

```python
# 常用技術指標

def sma(prices, period):
    """簡單移動平均"""
    return prices.rolling(period).mean()

def ema(prices, period):
    """指數移動平均"""
    return prices.ewm(span=period, adjust=False).mean()

def rsi(prices, period=14):
    """相對強弱指標 (0-100)"""
    delta = prices.diff()
    gain = delta.where(delta > 0, 0).rolling(period).mean()
    loss = (-delta.where(delta < 0, 0)).rolling(period).mean()
    rs = gain / loss
    return 100 - (100 / (1 + rs))

def bollinger_bands(prices, period=20, std_dev=2):
    """布林通道"""
    middle = sma(prices, period)
    std = prices.rolling(period).std()
    upper = middle + std_dev * std
    lower = middle - std_dev * std
    return upper, middle, lower

def macd(prices, fast=12, slow=26, signal=9):
    """MACD 指標"""
    ema_fast = ema(prices, fast)
    ema_slow = ema(prices, slow)
    macd_line = ema_fast - ema_slow
    signal_line = ema(macd_line, signal)
    histogram = macd_line - signal_line
    return macd_line, signal_line, histogram

def atr(high, low, close, period=14):
    """平均真實範圍 (波動度)"""
    tr1 = high - low
    tr2 = abs(high - close.shift())
    tr3 = abs(low - close.shift())
    tr = pd.concat([tr1, tr2, tr3], axis=1).max(axis=1)
    return tr.rolling(period).mean()
```

## 策略模式庫

### 趨勢跟蹤策略

```python
def trend_following_strategy(data, short_ma=20, long_ma=50):
    """
    雙均線趨勢策略

    規則：
    - 短均 > 長均 且 價格 > 短均 → 做多
    - 短均 < 長均 且 價格 < 短均 → 做空
    - 其他 → 空倉
    """
    data['ma_short'] = data['close'].rolling(short_ma).mean()
    data['ma_long'] = data['close'].rolling(long_ma).mean()

    conditions = [
        (data['ma_short'] > data['ma_long']) & (data['close'] > data['ma_short']),
        (data['ma_short'] < data['ma_long']) & (data['close'] < data['ma_short'])
    ]
    choices = [1, -1]
    data['position'] = np.select(conditions, choices, default=0)

    return data
```

### 均值回歸策略

```python
def mean_reversion_strategy(data, lookback=20, entry_z=2, exit_z=0):
    """
    均值回歸策略（布林通道）

    規則：
    - 價格觸碰下軌 (z < -2) → 做多
    - 價格觸碰上軌 (z > 2) → 做空
    - 回歸均值時平倉
    """
    data['ma'] = data['close'].rolling(lookback).mean()
    data['std'] = data['close'].rolling(lookback).std()
    data['z_score'] = (data['close'] - data['ma']) / data['std']

    position = 0
    positions = []

    for z in data['z_score']:
        if z < -entry_z and position == 0:
            position = 1  # 做多
        elif z > entry_z and position == 0:
            position = -1  # 做空
        elif abs(z) < exit_z:
            position = 0  # 平倉
        positions.append(position)

    data['position'] = positions
    return data
```

### 配對交易策略

```python
def pairs_trading_strategy(price_a, price_b, lookback=60, entry_z=2, exit_z=0.5):
    """
    配對交易策略

    假設：兩個高相關資產的價差會回歸
    """
    # 計算價差
    spread = price_a - price_b

    # 計算 z-score
    spread_mean = spread.rolling(lookback).mean()
    spread_std = spread.rolling(lookback).std()
    z_score = (spread - spread_mean) / spread_std

    # 生成信號
    # z < -2: 做多價差 (買A賣B)
    # z > 2: 做空價差 (賣A買B)
    position_a = np.where(z_score < -entry_z, 1,
                 np.where(z_score > entry_z, -1, 0))
    position_b = -position_a

    return position_a, position_b, z_score
```

## 因子計算範例

```python
# 動量因子
def momentum_factor(prices, lookback=252):
    """過去一年報酬率（排除最近一個月）"""
    return prices.shift(21).pct_change(lookback - 21)

# 價值因子
def value_factor(fundamentals):
    """E/P（本益比倒數）"""
    return fundamentals['earnings'] / fundamentals['price']

# 因子標準化
def normalize_factor(factor):
    """Z-score 標準化"""
    return (factor - factor.mean()) / factor.std()
```

## 風險平價配置

```python
def risk_parity_weights(returns, target_risk=0.10):
    """
    風險平價配置：每個資產貢獻相同風險
    """
    volatilities = returns.std() * np.sqrt(252)
    inverse_vol = 1 / volatilities
    weights = inverse_vol / inverse_vol.sum()

    # 調整到目標風險
    portfolio_vol = (weights * volatilities).sum()
    weights = weights * (target_risk / portfolio_vol)

    return weights
```

## 停損策略

```python
def trailing_stop(prices, positions, atr_multiplier=2):
    """
    ATR 移動停損
    """
    atr = calculate_atr(prices, period=14)
    stop_loss = []
    highest_since_entry = prices.iloc[0]

    for i, (price, pos, atr_val) in enumerate(zip(prices, positions, atr)):
        if pos > 0:  # 多頭
            highest_since_entry = max(highest_since_entry, price)
            stop = highest_since_entry - atr_multiplier * atr_val
            stop_loss.append(stop)
        elif pos < 0:  # 空頭
            lowest_since_entry = min(lowest_since_entry, price)
            stop = lowest_since_entry + atr_multiplier * atr_val
            stop_loss.append(stop)
        else:
            stop_loss.append(None)
            highest_since_entry = price
            lowest_since_entry = price

    return stop_loss
```

## 策略衰退檢測

```python
def detect_regime_change(pnl_series, lookback=60):
    """
    檢測策略是否衰退
    """
    recent_sharpe = pnl_series.tail(lookback).mean() / pnl_series.tail(lookback).std()
    historical_sharpe = pnl_series.head(-lookback).mean() / pnl_series.head(-lookback).std()

    # 夏普比率下降超過 50% 警告
    if recent_sharpe < historical_sharpe * 0.5:
        return "WARNING: Strategy may be decaying"

    return "OK"
```

## 績效歸因分析

```python
def performance_attribution(returns, benchmark_returns, positions):
    """
    績效歸因分析
    """
    # Alpha: 超額報酬
    alpha = returns.mean() - benchmark_returns.mean()

    # 選股貢獻
    selection = (returns - benchmark_returns).mean()

    # 擇時貢獻
    timing = (positions * (returns - returns.mean())).mean()

    # 資訊比率
    tracking_error = (returns - benchmark_returns).std()
    information_ratio = alpha / tracking_error if tracking_error > 0 else 0

    return {
        'alpha': alpha * 252,  # 年化
        'selection': selection * 252,
        'timing': timing * 252,
        'information_ratio': information_ratio * np.sqrt(252)
    }
```

## 簡單移動平均交叉策略

```python
def sma_crossover_strategy(data, short=10, long=30):
    """
    短均線上穿長均線 → 買入
    短均線下穿長均線 → 賣出
    """
    data['SMA_short'] = data['close'].rolling(short).mean()
    data['SMA_long'] = data['close'].rolling(long).mean()

    data['signal'] = 0
    data.loc[data['SMA_short'] > data['SMA_long'], 'signal'] = 1
    data.loc[data['SMA_short'] < data['SMA_long'], 'signal'] = -1

    return data
```

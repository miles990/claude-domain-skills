---
schema: "1.0"
name: quant-trading
version: "1.1.0"
description: 量化交易策略開發、回測與風險管理
triggers:
  keywords:
    primary: [quant, trading, 量化, 交易, backtest, 回測, algo-trading, 演算法交易]
    secondary: [strategy, 策略, factor, 因子, arbitrage, 套利, hedge, 對沖]
  context_boost: [python, pandas, numpy, finance, investment, stock, futures]
  context_penalty: [design, marketing, frontend]
  priority: high
keywords: [finance, trading, quantitative, investment]
dependencies:
  software-skills: [python, database, data-analysis]
author: claude-domain-skills
---

# 量化交易 Quant Trading

> 系統化、數據驅動的交易策略開發

## 適用場景

- 開發交易策略（趨勢跟蹤、均值回歸、套利）
- 策略回測與績效分析
- 風險管理與部位控制
- 因子研究與 Alpha 挖掘

## 策略開發流程

```
┌─────────────────────────────────────────────────────────────────┐
│  量化策略開發流程                                               │
│                                                                 │
│  1. 假說形成 → 2. 數據準備 → 3. 策略編寫                       │
│       ↓                                                         │
│  6. 實盤監控 ← 5. 風險控制 ← 4. 回測驗證                       │
└─────────────────────────────────────────────────────────────────┘
```

## 核心知識

### 策略類型

| 類型 | 說明 | 風險 |
|------|------|------|
| **趨勢跟蹤** | 順勢而為，追漲殺跌 | 震盪市場虧損 |
| **均值回歸** | 價格偏離後回歸 | 趨勢市場虧損 |
| **統計套利** | 配對交易、價差收斂 | 相關性崩潰 |
| **高頻交易** | 微秒級別的價差捕捉 | 技術風險高 |

### 回測要點

```python
# 回測檢查清單
checklist = {
    "數據品質": "是否有生存者偏差？",
    "前視偏差": "是否使用了未來數據？",
    "過度擬合": "參數是否過度優化？",
    "交易成本": "是否包含手續費、滑價？",
    "樣本外測試": "是否保留測試集？",
}
```

### 風險指標

| 指標 | 公式 | 良好標準 |
|------|------|----------|
| **夏普比率** | (收益 - 無風險) / 標準差 | > 1.5 |
| **最大回撤** | 峰值到谷值的最大跌幅 | < 20% |
| **卡瑪比率** | 年化收益 / 最大回撤 | > 1.0 |
| **勝率** | 獲利交易 / 總交易 | > 50% |

## 最佳實踐

1. **先簡單後複雜** - 從簡單策略開始，逐步增加複雜度
2. **樣本外驗證** - 永遠保留一段數據做最終測試
3. **考慮交易成本** - 回測時加入真實的手續費和滑價
4. **分散風險** - 不要把所有資金押在單一策略
5. **持續監控** - 實盤後監控策略表現，設定停損條件

## 常見錯誤

| 錯誤 | 正確做法 |
|------|----------|
| ❌ 回測收益驚人就上線 | ✅ 檢查是否過度擬合 |
| ❌ 忽略交易成本 | ✅ 加入真實手續費和滑價 |
| ❌ 用全部數據訓練 | ✅ 分割訓練/驗證/測試集 |
| ❌ 單一策略 All-in | ✅ 多策略組合分散風險 |

## Sharp Edges

### SE-1: 回測過度擬合
- **嚴重度**: critical
- **情境**: 策略在回測中表現優異（夏普 > 3），但實盤虧損
- **原因**: 參數針對歷史數據過度優化，捕捉的是噪音而非信號
- **症狀**:
  - 回測夏普比率異常高（> 3）
  - 實盤表現遠低於回測（< 50%）
  - 參數對微小變動敏感
  - 交易次數過少，統計不顯著
- **檢測**: `sharpe.*[3-9]\.|sharpe.*\d{2,}`
- **解決**:
  ```python
  # ❌ 錯誤做法 - 只用一段數據優化
  best_params = optimize(full_data)

  # ✅ 正確做法 - Walk-forward 驗證
  results = []
  for train, test in walk_forward_split(data, n_splits=5):
      params = optimize(train)
      results.append(backtest(test, params))
  final_sharpe = np.mean([r.sharpe for r in results])
  ```

### SE-2: 前視偏差 (Look-ahead Bias)
- **嚴重度**: critical
- **情境**: 回測時無意使用了未來數據
- **原因**: 數據處理時沒有注意時間順序，或使用了 point-in-time 問題的數據
- **症狀**:
  - 回測報酬率完美
  - 使用當日收盤價作為當日信號
  - 基本面數據未考慮發布延遲
- **檢測**: 程式碼中搜尋 `shift\(-|iloc\[-1\].*today`
- **解決**:
  ```python
  # ❌ 錯誤做法 - 使用當天收盤計算當天信號
  signal = prices['close'] > prices['close'].rolling(20).mean()

  # ✅ 正確做法 - 信號要延遲一天
  signal = prices['close'].shift(1) > prices['close'].shift(1).rolling(20).mean()
  ```

### SE-3: 生存者偏差
- **嚴重度**: high
- **情境**: 只使用當前存在的股票進行回測
- **原因**: 退市、下市的股票被排除，導致高估策略表現
- **症狀**:
  - 回測報酬明顯高於實際可達成
  - 小型股或低價股策略表現特別好
  - 沒有包含退市股票
- **解決**:
  - 使用包含退市股票的完整數據庫
  - 考慮退市時的損失（通常 -100%）
  - 使用 Point-in-Time 數據供應商

### SE-4: 忽略交易成本與滑價
- **嚴重度**: high
- **情境**: 高頻換手策略看起來很賺錢
- **原因**: 沒有計入手續費和滑價，實際成本吃掉所有利潤
- **症狀**:
  - 年換手率 > 1000%
  - 單筆獲利 < 0.5%
  - 回測用收盤價成交
- **解決**:
  ```python
  # 計入真實成本
  commission = 0.001  # 0.1% 手續費
  slippage = 0.002    # 0.2% 滑價
  total_cost = commission + slippage  # 每筆 0.3%

  # 調整後報酬
  net_return = gross_return - (total_cost * turnover)
  ```

### SE-5: 過度自信於樣本內績效
- **嚴重度**: medium
- **情境**: 只看樣本內回測結果就決定上線
- **原因**: 沒有保留獨立的測試集
- **症狀**:
  - 沒有 out-of-sample 測試
  - 驗證集被重複使用多次
  - 測試集數據量太少
- **解決**:
  ```python
  # ✅ 正確的數據分割
  train = data['2015':'2019']      # 訓練 (60%)
  valid = data['2020':'2021']      # 驗證 (20%)
  test = data['2022':'2023']       # 測試 (20%) - 只用一次！

  # 開發時只用 train + valid
  # 最終決策前才用 test
  ```

## 工具推薦

- **Backtrader** - Python 回測框架
- **QuantConnect** - 雲端量化平台
- **TradingView** - 圖表分析和策略測試
- **Zipline** - Quantopian 開源回測引擎

## Python 範例

```python
# 簡單移動平均交叉策略
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

## 參考資源

- [Quantitative Trading - Ernest Chan](https://www.amazon.com/Quantitative-Trading-Build-Algorithmic-Business/dp/1119800064)
- [Advances in Financial Machine Learning - Marcos Lopez de Prado](https://www.amazon.com/Advances-Financial-Machine-Learning-Marcos/dp/1119482089)

## 因子投資

### 常見因子

| 因子 | 說明 | 邏輯 |
|------|------|------|
| **價值** | P/E, P/B 低 | 便宜股票長期表現好 |
| **動量** | 過去漲的繼續漲 | 趨勢持續性 |
| **品質** | ROE 高、負債低 | 好公司溢價 |
| **規模** | 小型股溢價 | 流動性補償 |
| **波動** | 低波動異常 | 低風險高報酬 |

### 因子計算範例

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

## 部位管理

### Kelly 公式

```
┌─────────────────────────────────────────────────────────────────┐
│  Kelly Criterion                                                 │
│                                                                 │
│  f* = (p × b - q) / b                                           │
│                                                                 │
│  f* = 最佳投注比例                                               │
│  p  = 勝率                                                       │
│  q  = 敗率 (1 - p)                                               │
│  b  = 賠率（盈虧比）                                             │
│                                                                 │
│  範例：勝率 55%, 賠率 1.5                                        │
│  f* = (0.55 × 1.5 - 0.45) / 1.5 = 25%                           │
│                                                                 │
│  實務：使用 Half-Kelly (12.5%) 降低波動                         │
└─────────────────────────────────────────────────────────────────┘
```

### 風險平價

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

## 實盤注意事項

### 執行風險

| 風險 | 說明 | 對策 |
|------|------|------|
| **滑價** | 成交價與預期價差異 | 限價單、分批執行 |
| **流動性** | 無法成交足夠數量 | 避免小型股、設定上限 |
| **系統故障** | 程式/網路中斷 | 備援系統、人工監控 |
| **黑天鵝** | 極端事件 | 部位上限、停損機制 |

### 策略衰退檢測

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

## 回測報告模板

```markdown
## 策略回測報告

### 基本資訊
- 策略名稱：
- 回測期間：
- 交易標的：
- 初始資金：

### 績效指標
| 指標 | 數值 |
|------|------|
| 年化報酬 | |
| 夏普比率 | |
| 最大回撤 | |
| 卡瑪比率 | |
| 勝率 | |
| 盈虧比 | |

### 風險分析
- 最大連續虧損天數：
- 最大單筆虧損：
- VaR (95%)：

### 交易統計
- 總交易次數：
- 年均交易次數：
- 平均持倉時間：

### 結論與建議
[策略優缺點分析]
```

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

## 風險管理框架

```
┌─────────────────────────────────────────────────────────────────┐
│  風險管理三層架構                                                │
│                                                                 │
│  Layer 1: 交易層                                                │
│  ├─ 單筆停損：最大損失 2% 帳戶價值                              │
│  ├─ 單筆停利：根據波動度設定                                    │
│  └─ 移動停損：保護利潤                                          │
│                                                                 │
│  Layer 2: 策略層                                                │
│  ├─ 最大持倉：單策略不超過 20% 總資金                          │
│  ├─ 最大回撤：策略回撤超過 15% 減半部位                        │
│  └─ 相關性：避免高度相關的多個部位                              │
│                                                                 │
│  Layer 3: 組合層                                                │
│  ├─ VaR 限制：每日 VaR 不超過 2%                               │
│  ├─ 壓力測試：極端情境下的損失                                  │
│  └─ 流動性預留：保持 20% 現金                                   │
└─────────────────────────────────────────────────────────────────┘
```

### 停損策略

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

## 過度擬合診斷

```markdown
## 過度擬合警示信號

| 信號 | 說明 | 解決方案 |
|------|------|----------|
| 回測夏普 > 3 | 現實中很難達到 | 檢查數據洩漏 |
| 參數敏感 | 改一點參數結果大變 | 使用穩健參數範圍 |
| 交易次數少 | 樣本不足統計意義 | 延長回測期間 |
| 樣本外暴跌 | 訓練/測試落差大 | 重新審視策略邏輯 |

## 防止過度擬合的方法

1. **Walk-Forward Analysis**
   - 滾動視窗訓練和測試
   - 模擬真實使用情境

2. **Cross-Validation**
   - K-fold 交叉驗證
   - 時間序列要注意順序

3. **參數穩健性測試**
   - 測試參數附近的表現
   - 避免選擇極端值

4. **多市場驗證**
   - 在不同市場測試
   - 策略邏輯應該普適
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

## 機器學習在量化的應用

```markdown
## ML 策略開發注意事項

### 可行應用
- 因子組合優化
- 風險預測（波動度預測）
- 交易執行優化
- 另類數據處理（文本、圖像）

### 常見陷阱
| 陷阱 | 說明 |
|------|------|
| **數據洩漏** | 訓練時無意使用未來資訊 |
| **樣本偏差** | 只用特定市場狀態的數據 |
| **過擬合** | 複雜模型記住噪音 |
| **非穩態** | 金融數據分布會變化 |

### 特徵工程建議
```python
# 良好的特徵
- 技術指標（RSI, MACD, Bollinger %B）
- 基本面比率（P/E, P/B 的 Z-score）
- 動量特徵（多時間框架報酬）
- 波動特徵（已實現波動、隱含波動）

# 避免的特徵
- 原始價格（非穩態）
- 未標準化的數值
- 與目標高度相關的滯後變量（洩漏）
```

## 實盤 Checklist

```markdown
## 策略上線前檢查

### 回測驗證
- [ ] 樣本外測試通過
- [ ] 交易成本已包含
- [ ] 無前視偏差
- [ ] 滑價估計合理

### 風控設置
- [ ] 單筆停損設定
- [ ] 策略最大回撤停損
- [ ] 每日虧損上限
- [ ] 部位上限設定

### 系統準備
- [ ] 資金已到位
- [ ] API 權限正確
- [ ] 備援系統就緒
- [ ] 監控告警設定

### 心理準備
- [ ] 接受初期可能虧損
- [ ] 不會因單筆虧損改策略
- [ ] 設定檢視週期（如月度）
- [ ] 有明確的停用標準
```

## 免責聲明

```
⚠️ 量化交易涉及高風險，歷史績效不代表未來表現。
   本內容僅供教育參考，不構成投資建議。
   請在充分了解風險後謹慎投資。
```

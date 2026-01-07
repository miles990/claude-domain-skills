---
schema: "1.0"
name: quant-trading
version: "1.0.0"
description: 量化交易策略開發、回測與風險管理
triggers: [量化, 交易, 回測, 策略, 因子, 套利, 程式交易, 演算法交易, quant, trading, backtest, strategy, factor, arbitrage, algo-trading]
keywords: [finance, trading, quantitative, investment]
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

## 免責聲明

```
⚠️ 量化交易涉及高風險，歷史績效不代表未來表現。
   本內容僅供教育參考，不構成投資建議。
   請在充分了解風險後謹慎投資。
```

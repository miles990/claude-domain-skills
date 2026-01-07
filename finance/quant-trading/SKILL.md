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

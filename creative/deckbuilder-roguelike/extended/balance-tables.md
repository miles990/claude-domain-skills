# Deckbuilder Roguelike - Balance Tables

> Numerical reference tables for card, relic, and enemy balancing.

---

## Energy Cost Distribution

| Cost | Ratio | Position | Notes |
|------|-------|----------|-------|
| 0 | 10-15% | Support/Conditional trigger | High combo potential |
| 1 | 40-50% | Main cards/Basic effects | Bread and butter |
| 2 | 25-30% | Strong/Compound effects | Significant investment |
| 3 | 10-15% | Finishers/Ultimate | Turn-defining |
| X | 5% | Variable/Dump resources | End-of-turn plays |

---

## Base Value Framework (Per 1 Energy)

| Effect Type | Value | Notes |
|-------------|-------|-------|
| Damage | 6-8 | Base attack reference |
| Block | 5-6 | Base defense reference |
| Draw | 1 card | Card advantage |
| Energy Generation | 1 energy (this turn) | Tempo gain |
| Light Debuff | 1 turn duration | Vulnerable, Weak |
| Small Ongoing Effect | - | Context dependent |

---

## Keyword Value Adjustments

| Keyword | Value Adjustment | Role |
|---------|------------------|------|
| Exhaust | -0.5 energy value | Cost (removes from deck) |
| Ethereal | -0.3 energy value | Cost (may lose card) |
| Innate | +0.3 energy value | Benefit (guaranteed draw) |
| Retain | +0.2 energy value | Benefit (keep options) |
| Upgrade | +0.5~1.0 energy value | Standard power increase |

---

## Card Rarity Distribution

| Rarity | Color | Appearance Rate | Characteristics |
|--------|-------|-----------------|-----------------|
| Basic | Gray | Starting cards only | Simple, direct |
| Common | Gray | 60% of card pool | Build foundations |
| Uncommon | Blue | 37% of card pool | Strategy defining |
| Rare | Gold | 3%* of card pool | Build core |

> *Pity system: +1% rare chance for each common drawn

---

## Damage Calculation Reference

```
Final Damage = (Base + Strength) * Weak * Vulnerable - Block

Weak modifier: 0.75 (attacker has Weak)
Vulnerable modifier: 1.5 (defender has Vulnerable)
```

### Example Calculations

| Scenario | Base | Str | Weak | Vuln | Block | Result |
|----------|------|-----|------|------|-------|--------|
| Basic | 6 | 0 | No | No | 0 | 6 |
| +Strength | 6 | 3 | No | No | 0 | 9 |
| Vulnerable | 6 | 0 | No | Yes | 0 | 9 |
| Blocked | 6 | 3 | No | Yes | 5 | 8 |
| Weakened | 6 | 3 | Yes | No | 0 | 6 |

---

## Block Calculation Reference

```
Final Block = (Base + Dexterity) * Frail

Frail modifier: 0.75 (character has Frail)
```

---

## Progression Curve by Act

### Enemy Stats

| Act | Enemy HP | Enemy Damage | Elite HP | Elite Damage |
|-----|----------|--------------|----------|--------------|
| 1 | 30-50 | 8-15 | 60-80 | 15-20 |
| 2 | 50-100 | 15-25 | 100-150 | 25-35 |
| 3 | 100-200 | 25-40 | 200-300 | 35-50 |

### Boss Stats

| Boss | HP | Damage Range | Special |
|------|-----|--------------|---------|
| Act 1 | 200-300 | 20-30 | Single phase |
| Act 2 | 400-500 | 30-45 | May have phases |
| Act 3 | 600-800 | 40-60 | Multiple phases |
| Final | 1000+ | 50-80 | Complex mechanics |

---

## Relic Rarity & Sources

| Rarity | Source | Design Goal |
|--------|--------|-------------|
| Starting | Character default | Define character style |
| Common | Elite/Shop | General power boost |
| Uncommon | Elite/Shop | Build defining |
| Rare | Boss | Game changer |
| Event | Events only | Risk/Reward trade-off |
| Shop | Shop only | Convenience/Repair |
| Boss | Boss only | Very strong with cost |

---

## Balance Warning Thresholds

### Card Metrics

| Metric | Warning Threshold | Action |
|--------|-------------------|--------|
| Pick Rate | > 80% | Too strong - nerf |
| Pick Rate | < 5% | Too weak or unclear - buff |
| Win Rate Delta | > 10% | Needs adjustment |

### Relic Metrics

| Metric | Warning Threshold | Action |
|--------|-------------------|--------|
| Pick Rate | > 90% | Auto-pick - add trade-off |
| Skip Rate | > 50% | Unclear value - redesign |

---

## Adjustment Magnitude Guidelines

| Adjustment Type | Magnitude | When to Use |
|-----------------|-----------|-------------|
| Minor Tweak | ±10-15% | Fine-tuning |
| Moderate Change | ±20-30% | Notable rebalance |
| Major Redesign | Rework effect | Last resort |

### Avoid These Mistakes

- Changing too many things at once
- Making changes without data
- Over-reacting to community complaints
- Knee-jerk nerfs to popular cards

---

## Analytics Tracking Checklist

```yaml
card_metrics:
  pick_rate: Selection rate (when offered)
  win_rate: Win rate when holding this card
  play_rate: Uses per combat
  upgrade_priority: Upgrade frequency

relic_metrics:
  pick_rate: Selection rate
  win_rate: Win rate when holding
  synergy_with: Common pairings

balance_flags:
  - "Pick rate > 80% -> Likely too strong"
  - "Pick rate < 5% -> Likely too weak or unclear"
  - "Win rate delta > 10% -> Needs adjustment"
```

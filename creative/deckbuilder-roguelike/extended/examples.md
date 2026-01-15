# Deckbuilder Roguelike - Examples & Case Studies

> Detailed examples, case studies, and reference implementations.

---

## Build Archetype Examples

### Strength Build (Strength Flow)

```
Core: Stack Strength buff
Key Cards: Strength gain, multi-hit attacks
Synergy: Strength + Multi-Strike = Burst damage

Example Card Combo:
1. Inflame (+2 Strength, Power)
2. Limit Break (Double Strength)
3. Heavy Blade (Damage scales with Strength)
```

### Block Build (Block Flow)

```
Core: Excessive blocking, block retention
Key Cards: High block cards, block doubling
Synergy: Barricade + Stack block each turn

Example Card Combo:
1. Barricade (Block doesn't expire)
2. Entrench (Double current Block)
3. Body Slam (Deal damage = Block)
```

### Exhaust Build (Consume Flow)

```
Core: Exhaust triggers effects
Key Cards: Exhaust payoff cards, exhaust enablers
Synergy: Each exhaust +X effect

Example Card Combo:
1. Feel No Pain (+3 Block per Exhaust)
2. Dark Embrace (+1 Draw per Exhaust)
3. Corruption (Skills cost 0, Exhaust)
```

### Draw Build (Cycling Flow)

```
Core: Massive draw, thin deck
Key Cards: Draw engines, 0-cost cards
Synergy: Thin deck + Infinite loop

Example Card Combo:
1. Reflex (When discarded, draw 2)
2. Acrobatics (Draw 3, discard 1)
3. All-Out Attack (Deal damage to ALL)
```

### Poison/DOT Build

```
Core: Stack damage over time
Key Cards: Apply poison, poison multiplication
Synergy: Poison doubling + Survive long enough

Example Card Combo:
1. Noxious Fumes (+2 Poison to ALL each turn)
2. Catalyst (Double target's Poison)
3. Footwork (+Dexterity for survival)
```

---

## Synergy Matrix Analysis

### Synergy Strength Categories

| Category | Description | Card Examples |
|----------|-------------|---------------|
| **Safe Pick** | Useful independently | Strike+, Defend+ |
| **Core Build** | Defines the Build | Barricade, Corruption |
| **High Risk/Reward** | Needs setup, but powerful | Infinite combos |

### Design Guidelines

- Each Build needs 2-3 "Core Build" cards
- "Safe Pick" cards maintain baseline playability
- "High Risk/Reward" cards create excitement

---

## Map Structure Examples

### Standard 3-Act Structure

```
Act 1: Foundation (15-17 floors)
- Simple enemies teach mechanics
- First Elite around floor 5
- Boss tests basic skills

Act 2: Development (17-19 floors)
- Enemy combinations
- Multiple Elite paths
- Boss tests Build coherence

Act 3: Mastery (18-20 floors)
- Complex enemy patterns
- Dangerous Elite gauntlets
- Final Boss tests everything
```

### Node Distribution (Per Act)

| Node Type | Act 1 | Act 2 | Act 3 |
|-----------|-------|-------|-------|
| Combat | 50% | 45% | 40% |
| Elite | 10% | 15% | 20% |
| Event | 20% | 20% | 20% |
| Shop | 10% | 10% | 10% |
| Rest | 10% | 10% | 10% |

---

## Meta Progression Examples

### Unlock System

```yaml
# Cross-run unlock system
meta_progression:

  # Unlock new content
  unlocks:
    - condition: "Defeat Act 1 Boss"
      reward: "Unlock Character B"

    - condition: "Defeat Act 3 Boss"
      reward: "Unlock Challenge Mode"

    - condition: "Win with Character A"
      reward: "Unlock 5 new cards"

  # Achievement system
  achievements:
    - name: "Minimalist"
      condition: "Win with 15 or fewer cards"

    - name: "Perfectionist"
      condition: "Win without taking damage"
```

### Ascension/Difficulty Scaling

```
Level 0: Base game
Level 1: Enemies have +1 HP
Level 5: Elite fights give worse rewards
Level 10: Boss has new attack patterns
Level 15: Start with curse card
Level 20: All modifiers combined
```

---

## Successful Game Analysis

### Slay the Spire

**Why it works:**
- Perfect information balance (show enemy intent)
- Meaningful deck building choices
- Every run feels different
- High skill ceiling, low skill floor

**Key innovations:**
- Enemy intent system
- Exhaust as resource
- Relic synergies

### Monster Train

**Why it works:**
- Multi-floor tactical layer
- Dual faction combinations
- Spell vs Unit balance

**Key innovations:**
- Floor defense system
- Champion upgrade paths
- Clan combination system

### Inscryption

**Why it works:**
- Meta-narrative integration
- Rule-breaking moments
- Emotional engagement

**Key innovations:**
- Sacrifice mechanic
- Meta progression surprises
- Genre-blending

---

## Common Mistakes & Fixes

### Case Study: Overpowered Card

**Problem:** "Super Strike" - 1 cost, deal 12 damage
- Pick rate: 95%
- Win rate when picked: 70%
- Defines "correct" strategy

**Fix Options:**
1. Nerf damage to 9 (align with baseline)
2. Add cost increase (2 energy)
3. Add drawback (Exhaust, or lose HP)
4. Make conditional (deals 12 if enemy Vulnerable)

**Result:** Changed to 1 cost, 8 damage, +4 if enemy Vulnerable

### Case Study: Underpowered Card

**Problem:** "Meditation" - 2 cost, draw 1 card
- Pick rate: 2%
- Strictly worse than alternatives
- No clear use case

**Fix Options:**
1. Reduce cost to 0
2. Increase draw to 3
3. Add secondary effect
4. Change to Power with ongoing effect

**Result:** Changed to 1 cost, draw 2, Retain

# Deckbuilder Roguelike - Design Templates

> Detailed templates for card, relic, character, and enemy design.

---

## Card Design Template

```yaml
card:
  name: Card Name
  type: Attack | Skill | Power
  rarity: Basic | Common | Uncommon | Rare
  cost: 0-3 or X

  base_effect:
    description: Base effect description
    damage: Damage value (if applicable)
    block: Block value (if applicable)

  upgraded_effect:
    description: Upgraded effect
    improvements: [+3 damage, -1 cost, additional effect]

  keywords: [Exhaust, Ethereal, Innate, Retain]

  synergy_tags: [Strength, Block, Exhaust, Poison]

  design_intent: What Build does this card support
```

### Card Balance Checklist

```markdown
## Card Balance Checklist

### Value Reasonableness
- [ ] Effect/cost ratio matches baseline
- [ ] Upgrade adds ~0.5-1.0 energy value
- [ ] Reasonable compared to same-cost cards

### Build Positioning
- [ ] Clearly belongs to a Build archetype
- [ ] Has Synergy with 2-3 cards
- [ ] Not auto-pick (unconditionally strong)

### Player Experience
- [ ] Easy to understand effect
- [ ] Interesting decisions (not mindless use)
- [ ] Clear visual feedback

### Rarity Match
- [ ] Common: Simple and direct
- [ ] Uncommon: Conditional/complex effects
- [ ] Rare: Build core/game changer
```

---

## Relic Design Template

```yaml
relic:
  name: Relic Name
  rarity: common | uncommon | rare | boss | shop | event

  effect:
    trigger: Trigger timing
    # Common triggers: battle start, turn start, play card, on damage, on kill
    action: Specific effect

  synergy:
    - What cards/strategies it synergizes with

  anti_synergy:
    - What conflicts or makes it useless

  flavor_text: Background story
```

### Relic Examples by Category

```yaml
# Energy Relics
Lantern:
  rarity: common
  effect: "At combat start, gain 1 Energy"
  synergy: [high-cost cards, turn 1 burst]

# Draw Relics
Bag of Preparation:
  rarity: uncommon
  effect: "At combat start, draw 2 additional cards"
  synergy: [Innate cards, opening combos]

# Build-Defining Relics
Shuriken:
  rarity: uncommon
  effect: "Every 3 Attack cards played, gain 1 Strength"
  synergy: [low-cost attacks, multi-hit attacks]

# Boss Relics (powerful with drawbacks)
Runic Dome:
  rarity: boss
  effect: "+1 Energy per turn, but cannot see enemy intents"
  trade_off: Energy vs Information
```

---

## Character Design Template

```yaml
character:
  name: Character Name

  unique_mechanic:
    name: Exclusive mechanic name
    description: Mechanic explanation
    # Example: Orb system, Stance system

  starting_relic:
    name: Starting relic
    effect: Effect description

  starting_deck:
    strikes: 5  # Basic attack
    defends: 5  # Basic defense
    unique: [Exclusive starting cards]

  build_archetypes:
    - name: Build A
      core_cards: [Core card list]
      key_relics: [Key relics]

    - name: Build B
      core_cards: [Core card list]
      key_relics: [Key relics]

  card_pool:
    commons: 20-25
    uncommons: 25-30
    rares: 15-20

  playstyle: Playstyle description
```

### Character Differentiation Framework

Each character needs:
- Unique mechanic (exclusive system)
- Unique card pool (~75 cards)
- 2-3 main Build paths
- Starting relic (defines style)
- Unique gameplay feel

StS Character Examples:
- Ironclad: Strength stacking, self-heal
- Silent: Poison, discard, multi-hit
- Defect: Orb system (unique mechanic)
- Watcher: Stance switching (unique mechanic)

---

## Enemy Design Template

```yaml
enemy:
  name: Enemy Name
  type: normal | elite | boss
  hp: Health

  intent_pool:
    - intent: attack
      damage: 10
      frequency: 40%

    - intent: defend
      block: 8
      frequency: 20%

    - intent: buff
      effect: "+2 Strength"
      frequency: 20%

    - intent: debuff
      effect: "Player Weak for 2 turns"
      frequency: 20%

  ai_pattern: |
    Turn 1: Always buff
    Turn 2-3: Attack
    HP < 50%: More aggressive attacks

  design_intent: |
    What does this teach players? What skill does it test?
```

### Enemy AI Pattern Types

| Pattern Type | Description | Use Case |
|--------------|-------------|----------|
| **Cyclic** | Fixed sequence: A -> B -> C -> A... | Tutorial enemies, predictable |
| **Probabilistic** | Random based on weights | Unpredictable, adds challenge |
| **Conditional** | Changes behavior based on state | Requires understanding triggers |
| **Mixed** | Combines multiple patterns | Boss fights |

Examples:
- Cyclic: "Attack -> Defend -> Buff -> Loop"
- Probabilistic: "60% Attack / 30% Defend / 10% Ultimate"
- Conditional: "Rage mode when HP < 50%"
- Mixed: "Phase 1 cyclic, Phase 2 conditional trigger"

---

## Card Design Example Process

```yaml
# Design Process Demo

## 1. Determine Position
target_build: Strength Build
rarity: Uncommon
desired_role: Build accelerator

## 2. First Draft
card_v1:
  name: Berserk Stance
  cost: 1
  type: Skill
  effect: "Gain 2 Strength. Take +25% damage this turn"

## 3. Value Check
analysis:
  - 1 energy for 2 Strength -> Slightly above baseline
  - Has drawback (+25% damage taken) -> Balanced
  - Consider stacking effect -> Might be too strong

## 4. Adjustment
card_v2:
  name: Berserk Stance
  cost: 1
  type: Skill
  effect: "Gain 2 Strength. Gain 1 Vulnerable"
  upgrade: "Gain 3 Strength"

## 5. Synergy Check
synergies:
  - Strong Synergy with "Multi-hit attacks" OK
  - Conflicts with "Block Build" (acceptable) OK
  - Not single-card OP OK

## 6. Final Confirmation
final_check:
  - [ ] Clear and understandable effect
  - [ ] Clear Build positioning
  - [ ] Balanced values
  - [ ] Meaningful upgrade
```

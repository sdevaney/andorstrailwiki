# Combat

Combat in Andor's Trail is divided into turns. If the player engages in battle, they start their turn. If a monster participates in combat, the monster begins with its turn. On the player's turn, the player is initially given several Action Points (AP) to spend as they see fit. Actions that use up action points could be attacking, using a potion, or moving to an adjacent tile. The player's turn lasts until they have no AP left to spend. Then combat proceeds with the monsters' turn. On the monsters' turn, all monsters are also given an initial amount of AP to spend. All monsters that are adjacent to the player attack in sequence until no monsters have any AP left to do any further actions. The combat revolves this way until either all the monsters have been killed or the player has been killed.

If all monsters are killed, the player receives experience and loot. The amount of experience and loot items (including gold) is determined by monster type.

If the player is killed in combat, the player loses 30% of the built-up experience of the current level. _Note_ that the percentage is within the current level, so you can never lose so much experience that you decrease in level

## Base Statistics and Equipment Effects

Each actor (player and monster) has Base combat statistics that determine how proficient the actor is at fighting. This is also called Unequipped combat statistics. These statistics are made up of the following components:

Attack cost (action points)\
Chance to hit (%)\
Critical chance (%)\
Critical multiplier\
Damage potential\
Block chance (%)\
Damage resistance\
The actor can wear weapons, clothing, and items that affect these statistics, thereby creating an Equipped combat statistic. Equipped combat statistics are calculated by adding the item's combat statistics to the actor's base combat statistics. The only exceptions to this rule are the following:

The attack cost is purely determined by the weapon's attack cost.

## Attack Action

When using the attack action in combat, the attack is handled in the following way:

Determine the probability that the attacker hits the target. Call this X. See below for how this is calculated.\
Roll a 100-sided dice.\
If the dice value is greater than X, the attack is considered a miss and no damage is done.\
Otherwise, the attack is considered a hit. Determine damage in the following way:

Using the attacker's damage potential, pick a random number in this interval. Call this D.\
If the attacker has a chance of doing a critical hit (has a critical chance > 0%), roll a 100-sided die. If the dice value is less than or equal to the critical chance, the attack is considered a critical hit. Multiply D by the attacker's critical multiplier.\
Subtract the target's damage resistance from D.\
The attack causes the target to lose D HP. If the target has zero or fewer HP left, the target dies.

### Chance To Hit

The chance to hit in Andor's Trail v0.6.11 is calculated as follows: determine damage based on the attacker's damage potential, which is usually specified as an interval. The attack damage is a random number in that interval. If the target has any damage resistance, the resulting damage is reduced by the target's damage resistance. The formula is as follows:&#x20;

```
Effective AC = (Your AC) - (Target BC) Actual AC = 50 * (1 + (2/pi) * ATAN((Effective AC - 50) / 40))
```

Where:

* **Your AC** = Your Attack Chance (0-100)
* **Target BC** = Target's Block Chance (0-100)
* **π** = Pi (3.14159...)
* **ATAN** = Arctangent function (inverse tangent)
* **Actual AC** = Final hit chance percentage (0-100)

### Explanation

1. **Calculate Effective AC**: Subtract the target's block chance from your attack chance.
   * Higher AC means a better chance to hit.
   * Higher BC means better defense.
2. **Apply ATAN Formula**: The formula uses arctangent to create a sigmoid curve.
   * This creates smooth probability transitions.
   * Prevents extreme cases (always hit or always miss).
   * Matches the game's balance philosophy.
3. **Result**: Returns value between 0 and 100 (percentage).

### Attack Damage Calculation <a href="#attack-damage-calculation" id="attack-damage-calculation"></a>

Damage dealt by an attack is calculated from weapon and character attributes.

```
Base Damage = RANDOM(Weapon Min Damage, Weapon Max Damage)
Final Damage = Base Damage * (1 + AD_Bonus / 100)
```

Where:

* **Weapon Min/Max Damage** = Defined in weapon JSON.
* **AD\_Bonus** = Attack Damage bonus from equipment and conditions.
* **RANDOM()** = Random value within range (inclusive).
* **Final Damage** = Total damage dealt to the target.

### Armor Defense Calculation <a href="#armor-defense-calculation" id="armor-defense-calculation"></a>

Defense against damage is calculated from armor and conditions.

```
// Some codeDamage Reduction = AC_Bonus / 200
Actual Damage = Base Damage * (1 - Damage Reduction)
```

Where:

* **AC\_Bonus** = Armor Class bonus from equipment and conditions (up to 200).
* **Damage Reduction** = Percentage reduction (0-1.0).
* **Actual Damage** = Damage received after armor reduction.

### Block Chance <a href="#block-chance" id="block-chance"></a>

Block Chance (BC) represents the probability of completely negating an attack.

#### Properties

* **Range**: 0-100
* **Calculation**: Subtracted from attacker's AC (see Hit Chance section).
* **Equipment**: Added through armor and accessories.
* **Conditions**: Some conditions reduce BC (e.g., Stunned).

### Action Points (AP) <a href="#action-points-ap" id="action-points-ap"></a>

Combat turns are based on Action Points and movement costs.

```
AP Per Turn = 10 + (Speed Bonus / 10)
Movement Cost = 1 AP per tile
Attack Cost = Varies by weapon
```

Where:

* **Speed Bonus** = Bonus from equipment and conditions.
* **Movement Cost** = Fixed at 1 AP per tile moved.
* **Attack Cost** = Defined in weapon specifications.

### Health and Healing <a href="#health-and-healing" id="health-and-healing"></a>

Health determines character survivability.

```
Max HP = Base HP + (Level * Level Factor) + (HP Bonus)
Current HP = MAX(0, Current HP - Damage)
Current HP = MIN(Max HP, Current HP + Healing)
```

Where:

* **Base HP** = Starting HP value.
* **Level** = Character level.
* **Level Factor** = HP gain per level (typically 1-2).
* **HP Bonus** = Bonus from equipment and conditions.

### Critical Hits <a href="#critical-hits" id="critical-hits"></a>

Some weapons or conditions enable critical hits.

```
Critical Chance = Critical Modifier (if applicable)
Critical Damage = Base Damage * 1.5
```

Where:

* **Critical Modifier** = Defined in weapon or condition.
* **Critical Damage** = 150% of normal damage.


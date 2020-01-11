# Combat

Combat in Andor's Trail is divided into turns. If the player engages in combat, the player starts with his or her turn. If a monster engages combat, the monster starts with their turn. In the player's turn, the player is initially given an amount of Action Points \(AP\) to spend as the player sees fit. Actions that use up action points could be attacking, using a potion or moving to an adjacent tile. The player's turn lasts until the player has no AP left to spend. Then combat proceeds with the monsters' turn. On the monsters' turn, all monsters are also given an initial amount of AP to spend. All monsters that are adjacent to the player attack in sequence until no monsters have any AP left to do any further actions. The combat revolves this way until either all the monsters have been killed, or the player has been killed.

If all monsters are killed, the player is rewarded with experience and loot. The amount of experience and loot items \(including gold\) is determined by monster type.

 If the player is killed in combat, the player loses 30% of the built up experience of the current level. _Note_ that the percentage is within the current level, so you can never lose so much experience that you decrease in level

## Base Statistics and Equipment Effects

Each actor \(player and monster\) has a Base combat statistics, that determine how proficient the actor is at fighting. This is also called Unequipped combat statistics. These statistics are made up of the following components:

Attack cost \(actions points\)  
Chance to hit \(%\)  
Critical chance \(%\)  
Critical multiplier  
Damage potential  
Block chance \(%\)  
Damage resistance  
The actor can wear weapons, clothing and items that affect these statistics, thereby creating a Equipped combat statistics. Equipped combat statistics is calculated by adding the item's combat statistics to the actor's base combat statistics. The only exceptions to this rule are the following:

Attack cost is purely determined by the weapon's attack cost.

## Attack Action

When using the attack action in combat, the attack is handled in the following way:

Determine the chance of the attacker hitting the target. Call this X. See below for how this is calculated.  
Roll a 100-sided dice.  
If the dice value is greater than X, the attack is considered a miss and no damage is done.  
Otherwise, the attack is considered a hit. Determine damage in the following way:

Using the attackers damage potential, pick a random number in this interval. Call this D.  
If the attacker has a chance of doing a critical hit \(has critical chance &gt; 0%\), roll a 100 sided dice. If the dice value is less than or equal to the critical chance, the attack is considered a critical hit. Multiply D by the attacker's critical multiplier.  
Subtract the target's damage resistance from D.  
The attack causes D HP to be lost on the target. If the target has 0 or less HP left, the target dies.

## Chance To Hit

 The chance to hit in Andor's Trail v0.6.11 is calculated in the following way: _Determine the attacker's chance to hit. Call this A. \(This value may be greaten than 100\)  
Determine the target's block chance. Call this B.  
Calculate C = A - B  
Calculate F = 50 \* \(1 + \(2/pi\) \* ATAN\( \(C - 50\) / 40 \) \)  
This function will produce a number between 0 and 100.  
If C is 50, then F will be 50.  
If C is high \(the attacker's chance to hit is higher than the target's block chance\), then F will be near 100.  
If C is low, then F will be 50.  
The chance to hit \(in percent\) is F._

## Damage

Damage is calculated by the attacker's damage potential, which is usually specified in an interval. The attack damage is a random number in that interval. If the target has any damage resistance, the resulting damage is reduced by the target's damage resistance

## Fleeing

When engaging combat with a tough monster, sometimes the best action is to flee and return later when you have built up your character and equipment more.

### How to flee

1. Engage in combat by attacking a monster, or wait until it's your time to start your attack turn.
2. Select a square to move to that doesn't have any monster on it.
3.  **Longpress that square.**
4. Notice how the square lights up yellow, thus indicating that you have selected it.
5. Also notice that the “Attack” button has changed to a “Move” button.
6. Tap the screen \(or tap the Move button\) to move to that square.
7. Hopefully, you should now be in a square that doesn't have any monster adjacent to it.
8. Tap the screen \(or tap “End combat”\) to end combat.
9. Combat ends. You have fled the fight.
10. Make sure to kill that bastard later :\)

## Selecting a Target

Longpressing an adjacent square also allows you to select a different monster to attack.


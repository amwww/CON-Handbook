---
description: >-
  Combat is the heart of CON, powering every single unit interaction. Having
  knowledge over how this works significantly gives you an edge over your
  opponents.
---

# ⚔️ Combat

## Overview

Combat in CON works on a tick-based system, in which damage is applied every hour, called a combat tick.

For this section, we will call individual units "troops", and a group of units a "stack" or an "army", and if interchangeable, a "unit".

## Troops, Stacks & Groups

When troops join together, they form a stack of units. However, there is a smaller "unit" of troops called a group.

### Type Groups

A bunch of troops of the type in a stack is called a "type group".

This is evident when a troop loses some health and then joins another stack.

Usually, when a type group loses health beyond one troop, the troop count decreases.

**>>** For example, if you have 3 infantry of 15 HP each, totalling 45 HP, and you lose 15 HP, becoming 30/45 HP, then you lose 1 infantry.

When a troop of less than full HP joins a type group, they become their own group within, ignoring the above rule, instead of just contributing to the health of a troop. This is because the one infantry still has the potential to heal.

**>>** For example, if you have 1 infantry at two-thirds health (10 HP) and joins 2 infantry at 20 HP, becoming 30/45 HP. This will **not reduce** the troop count, unlike the above example, as the one infantry that joined is grouped. This is because the 1 infantry that joined is its own separate type group.

However, if a type group engages in combat or splits, the group is broken as the game updates the groupings, and this may instantly cause troop loss.

**>>** Take the above example again, if that unit engages in combat, the group is broken, and the 1 infantry will no longer be protected, and revert to two infantry at 30/30 HP (ignoring any damage from combat).

> &#x20;This is useful to know, as if you have damaged troops, you shouldn't join them together for combat. You should aim to heal the units as soon as possible.

> You can also abuse this in combat by spliting your type groups. If you had 2 infantry at 16/30 HP, and the enemy is at 1/15 HP, meaning you would most definetly kill the enemy unit next comabt tick, but also your 2 infantry would take damage and get reduced to 1 infantry, you should split to get 2 armies of 1 infantry, so they would each take damage, without losing 1 infantry.

## Unit Attributes

### Strength

Every unit and troop has a strength, which is the estimated damage that the stack will do. The reason that this is "estimated" is because the actual damage that the unit will do heavily depends on **RNG**. See the section on actual damage.

### Hit Points

This is how many hit points, HP, a unit has.&#x20;

#### Stack HP

The HP of a stack is determined by the total HP of all the troops in that stack.

{% hint style="info" %}
Signature Units like the aircraft carrier cannot stack with each other, and neither can two officers or veterans.
{% endhint %}

#### Troop HP

Every troop has its own HP value. When mobilized, that troop will start at the max HP (100%).

CON stores HP values as both a percentage and a value. For combat purposes, the HP value is used, but when you upgrade your units through research, CON will update the Max HP of every unit already mobilized.

For example, an infantry with 15 HP and a percentage of 100% loses 3 HP. The HP value would be 12, and the percentage would be 80%. After that, you upgrade your infantry, which now has a Max HP of 17. The new **updated** HP value for that unit would be 80% \* 17 = 13.6, and not 12.

### Attack & Defense

Every troop has attack & defense. These attributes will be used during [different types of encounters](combat.md#combat-ticks).

{% hint style="info" %}
Soft targets usually have higher defense than attack damage.
{% endhint %}

> Being on defense is very beneficial, due to [entrenchment](combat.md#entrenchment) and a higher defense damage.

#### Health Penalty

When a unit is damaged, all of its strength, including defense and attack, will be reduced. The formula for calculating the multiplier is as follows:

$$
MissingHealthPenalty=25\%\,+\,\frac{75\%\,*\,CurrentHealth}{MaximumHealth}
$$

#### Efficiency Penalty

When an army gets excessively large, it begins to suffer strength and movement speed penalties. The maximum unit count for a stack is as follows, depending on its type:

| Unit Type | Maximum Stack |
| --------- | ------------- |
| Land      | 10            |
| Air       | 5             |
| Sea       | 5             |

{% hint style="info" %}
Note that transport convoys or planes are counted as sea and air types, respectively.
{% endhint %}

{% hint style="info" %}
Planes and helicopters on the ground are considered a land type.
{% endhint %}

The multiplier for its strength stat is as follows:

$$
CombatEffectivenessMultiplier=1-0.56\,*\,ln(\frac{StackSize}{MaxStackSize})\,\text{where}\,StackSize > MaxStackSize
$$

### Entrenchment

When very close or at a city center, a unit will receive an entrenchment bonus, a 25% reduction to incoming damage taken.

> Stationing your troops at the center of a province during combat provide massive bonuses!

## Combat Ticks

During each combat tick, each army will apply damage to the opponent's armies, using either the "attack" or "defense" stat, depending on the situation:

### Defending

If a unit is entrenched, and the other is not, the entrenched unit will be on defense, using the defense strength stat.

Defense damage is **always** calculated first.

> As troops deal less damage with lower HP, being on defense can further reduce your opponent's attack stat, further reducing your damage.

### Attacking

If a unit is not entrenched and is engaging with another unit, the unit that is not entrenched will be on offense, using the attack strength stat.

### Postup

If both engaging units are not entrenched, both defense and attack will be applied in the same combat tick.

### Multiple Army Engagement

Multiple armies can engage with each other. If this is the case, one side will engage with every other enemy unit, in the same combat tick.

{% hint style="danger" %}
Note that you **cannot** merge units during combat; you can only split them!
{% endhint %}

> If your units arrive at a combat site split, then they will take double the damage as if they were a single army. Armies will not merge when they are moving, so if you are planning to engage in combat / take a city when your armies are not already grouped together, find a province or city to group them first before sending them into combat.

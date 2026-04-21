---
description: This section will guide you into using the UI in CON.
---

# 🔘 Interface

## Unit Commands

### Move

This will move the battalion, ignoring any previous commands.

{% hint style="info" %}
If another nation claims any province or city along your unit's path that you are not at war with, your unit will stop, canceling its orders automatically, not declaring war on that nation.\
\
This sometimes means that your units will just stop suddenly, so know that this is probably the reason why. You'll have to re-path your units then.
{% endhint %}

{% hint style="info" %}
Using the move command also means that you will only attack the province if there are enemies there.
{% endhint %}

#### &#x20;Pathfinding Priority

This is how CON will choose the pathway that your unit(s) will take, in order from most important to least important. CON will optimize for the first one before the second.<br>

This is an example of what **priority** means. CON will first look at the first column for all possible pathways.

<table><thead><tr><th width="177.2578125">Declarations of War</th><th width="166.8125">Time of Arrival</th><th>Behaviour</th></tr></thead><tbody><tr><td>1</td><td>1s</td><td>This eliminates this option, as 0 is the lowest for the first column, no matter how short the time of arrival is. </td></tr><tr><td>0</td><td>1d</td><td>Then, once the lowest first priority options have been identified, CON will look for the second priority, and minimize that too.</td></tr><tr><td>0</td><td>25m</td><td>In this case 25m &#x3C; 1d, so this is the option CON will choose, even if there is a shorter arrival time available.</td></tr></tbody></table>

The priority is as follows:

1. The least number of countries declaring war on - Ideally, CON will try to pathfind a route so that the route will declare war on the **least** number of countries, with the smallest being 0. \
   \
   Note that if you are already at war with a country, CON will **not** count this as "declaring war" on a country.
2. Shortest time of arrival

For example:\
\
If the shortest path from A to B goes through province O, which is conquered by a nation X you are **not** at war with, CON will pick an alternative fastest route that doesn't declare war on them. \
\
A[^1] — [<mark style="color:$primary;">O</mark>](#user-content-fn-2)[^2] — B[^3] \
This will declare war on nation X, so CON will prefer this pathway instead:\
A-,\_\_<mark style="color:$success;">O</mark>\_\_\_,B\
This path goes around nation X without declaring war on it. As this is the shortest path that declares war on 0 nations, CON will pathfind your units this way.\
\
However, if you are already at war with nation X, going into province O doesn't declare war on anybody. As this is now the shortest path that declares war on 0 nations, CON will pathfind your units this way instead.\
A — <mark style="color:red;">O</mark> — B\
\
Note that the shortest time of arrival isn't always the shortest path, as the unit's speed is affected by terrain.

### Attack

This will move the battalion and use a unit's **ranged** attack to attack an enemy province, ignoring previous commands. If no units in your battalion have a range attack, it will use a melee attack instead.

{% hint style="danger" %}
If another nation claims any province or city along your unit's path that you are not at war with, your unit will **not** stop, subsequently declaring war on that nation.
{% endhint %}

See the section on [pathfinding priority](interface.md#pathfinding-priority) for how the battalion will move.

### Waypoint

{% embed url="https://drive.google.com/file/d/1K5PZoyk-eLLoCdlnLUNFGZshC5YXJEki/view" %}
A video demonstrating how to waypoint
{% endembed %}

When you move or attack, CON will find the path that will take the shortest amount of time from where your unit currently is to where your cursor is.\
\
Waypointing continues from the unit's existing pathway, finding the shortest path from where the current destination is to where your cursor is. Pressing confirms this path, and you can waypoint again to extend that path.

{% hint style="info" %}
Note that the waypoint button will not appear until you have an existing path through the move or attack commands.
{% endhint %}

You can do this as many times as you want, as a custom path is not possible without the waypoint command, due to CON choosing the path with the shortest time of arrival.

### Split

{% embed url="https://drive.google.com/file/d/1EQRWo39EraGMuvbCTa4Zhih_jE-OmVfB/view" %}
A video demonstrating how splitting works
{% endembed %}

### Rush

Rushing boosts your unit's speed by 50%, at a penalty of <mark style="color:$danger;">**5% max HP per hour**</mark>.

{% hint style="info" %}
If your unit does not have enough HP to sustain this, it will cancel the rush order.
{% endhint %}

> It is generally recommended only for stealing land, such as attempting to get a city before someone else, where rushing would allow that, or returning to a city entrenchment so you can get a defense order, which does more damage.

#### Rush Snapping

CON snaps troops to the center of a province, for convenience, if your troop is close enough to the center, when the order is updated. You can abuse this by activating rush when your troop is about 15 minutes away from the center of the province, which will automatically snap your unit there, conquering that piece of territory, and then <mark style="color:$warning;">**turning off rush**</mark>.&#x20;

### Delay

Using Delay, you can continue carrying on the order, but you can select an amount of time that your troop would stand still and wait. Usually recommended at times when your artillery, ships, and fighters are dealing heavy damage to the troop, and you are trying to avoid casualties in your division. It can be used so your troops can auto-move at a certain time, even when you are not in the game.

### Patrol

Used for air units, patrol will set your unit into a mode where it will automatically engage with any enemy unit listed in its stats. When the unit moves to its patrol location, the game will treat it as being everywhere in the radius at once, meaning it can be detected as long as your radar or other patrol reachers inside the patrol radius, showing up as the target being in the center of the patrol.

> This means you can hit another air unit patrolling while being out of its patrol radius. Aircraft radar contancts can also appear outside of your radar range.

## ꚙ

**↑** Imagine this is an enemy aircraft's patrol radius\
&#x20; **↑** Imagine this is your patrol radius or radar range

You will be able to hit this aircraft, as they are intersecting, even though you do not hit the center of the radius, and this aircraft will still show up outside your radar.

### Grouping

Grouping is how you merge troops to form a big unit. To do so, simply select the troops and move them to the same place. This place can be a provincial center or a city center, and once both arrive, they will merge.&#x20;

{% hint style="danger" %}
Note that you **cannot** merge (group) units during combat; you can only split them!
{% endhint %}

This is a video on how to merge:

{% embed url="https://drive.google.com/file/d/1XG3RsFFSPhJn4CacbCJOB1YtMQIQfksS/view" %}



### Retreat

When your unit is in close-quarters combat, the only way for the unit to stop attacking and taking damage is through this command. You may not cancel the order or move away without retreating. Doing so will lose significant HP, scaled to the max HP of your units.

> Do this when you know for sure that you will lose. It isn't worth it otherwise.

{% hint style="success" %}
This will **never** kill your entire unit, and can only make your unit lose troops.
{% endhint %}

### Cancel Orders

This just cancels all the units' move and attack orders.

{% hint style="warning" %}
However, if your unit is still in combat or can get into combat, canceling the orders will not take your units out of combat. If your troops are still in range to attack a known enemy **troop** (has to be an unidentified contact, not a radar contact or a province), it will do so.
{% endhint %}



[^1]: Unit Location

[^2]: Conquered by Nation X

[^3]: Destination

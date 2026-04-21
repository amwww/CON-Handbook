# 🏥 Healing

Healing allows your units to replenish their HP.

## Healing Rate

Cities heal at a rate of 1 HP/day/unit.

Provinces heal at a rate of 0 HP/day/unit.

Coastal Waters heal at a rate of 2 HP/day/unit, only if the unit is out of combat. This is applicable to ships and **maybe transport vehicles**.

Military Hospitals, built in cities, up to 5 levels, and Field Hospitals, built in provinces, up to 3 levels, increase the province or city's healing by 1 HP/day/unit/level.

## Healing Ticks

Every hour, if the unit is currently in a city or province, the unit will heal. The unit does **not** have to be entrenched or in a city center.

> You might want to consider one of your coalition members having a dedicated city with an airbase or airfield to heal troops by building a military hospital.

Each troop in a [type group](combat.md#type-groups) will heal by its current [healing rate](healing.md#healing-rate).

> This means that having 2 infantry will heal at 2 HP/day.  Meaning having more troops, even if they are already at full HP, will speed up the healing of your stack.

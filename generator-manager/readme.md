# Generator Manager
----
### Author
*BenCo#2544*
![Made by BenCo](https://i.imgur.com/gG2GDMos.png "Made by BenCo")
---
### Requirements
 - Basic YOLOL Chip [1]
---
### Overview
This script manages power levels of batteries and generators in a ship and attempts to keep battery levels at a high level whilst maintaining generator activity and preventing overusing generators and wasting fuel. Furthermore, it also allows users to specify one or more "priority generators" which will be run first before any other generators. This is because FB have confirmed that down the road there will be different fuel efficiencies and it may be more practical to optimise for efficiency in a lot of cases. Furthermore, it can make fuel management easier by reducing the number of generators you need to frequently check if one or more are prioritised and used exclusively in most cases (YMMV based on energy needs/production).

If you have priority generators set, they will be used like the following examples:
`1 Priority Generator + 1 Normal Generator`
- 100% Power usage = 100% Priority + 100% Normal
- 75% Power usage = 100% Priority + 50% Normal
- 50% Power usage = 100% Priority
- 25% Power usage = 50% Priority

You can also optionally define an override button and lever. The button is used to enable override and the lever sets the power usage/production. It is a 1:1 ratio, so if you set the lever to 90%, it will generate 90% of total power capacity, whilst still attempting to use Priority Generators where available as described above.
Note, using override can cause power outages which  will require a manual generator restart if the set power level is too low to maintain batteries. Caution is advised when taking manual control to ensure battery levels, or to resume script activity before power is lost.
---
### Instructions
##### Core
- Leave your batteries on their default data fields, `StoredBatteryPower` and `MaxBatteryPower`
- Set your Normal Generators (these run if the priority ones aren't enough or aren't used) to use `G` as their `generatorunitratelimit` value field name
- Set `PG` and `G` at the top of the script to the number of Priority and Normal Generators you have respectively. For example, if you have 2 Priority Generators and 3 Normal Generators, then set the first line as `PG = 2 G = 3`

##### Priority Generators
- Set your priority generators (these run first) to use `P` as their `generatorunitratelimit` value field name

##### Override
- Set your override button to use `Override` as its `buttonstate` field
- Set your override button to use `1` as it's `buttonstyle` to allow it to toggle without being held continuously
- Set your override lever to use `OverrideAmount` as its `levervalue` field
- Use the override lever to set the override amount and the override button to turn manual override on.
- If you don't need an override system, you don't need to add the levers. It'll run automatically if they aren't installed.

##### Tips / Notes
- Enjoy the power optimisation
- You can monitor generator usage through the variables `P` and `G` which are exposed to other devices such as progress bars and go from 0 to 100
- Make sure you have enough batteries because generators need time to warm up. (1 Second per percent usage per generator)

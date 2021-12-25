# Factorio
## Quick Links
* [Official Factorio Wiki](https://wiki.factorio.com/)
* [Factorio | Reddit](https://www.reddit.com/r/factorio/) - Reddit
* https://kirkmcdonald.github.io - Item calculator
* [Factorio Prints](https://factorioprints.com/)
* [Factorio Prints](https://www.factorio.school/) - newer Factorio School

## Command line
* ` to get prompt box
* Maps and showing grid - [Map structure - Factorio Wiki](https://wiki.factorio.com/Map_structure)
* Infinity chest
`/c game.player.insert(“infinity-chest”)”`

## Map Editor
`/editor`
[Map editor - Factorio Wiki](https://wiki.factorio.com/Map_editor)

## Design Hints
* 12 belt main bus. 4 belts, 2 space, 4 belts, 2 space, 4 belt
* 2 space buffer above/below belt.
* 1 addition space to first building
* Constant combinator hints
	* prongs face belt travel direction
	* ideally 2 spaces above main belt
	* 1 or 2 items for half or full belt
	* 1st item top of belt, 2nd item bottom of belt
* Blueprint belts: 3 spaces above main belt
* blueprint factory: starting 2nd space above main belt (where content combinator is)

## Sandbox Mode
* Play scenario, sandbox
* Enable cheats
* 
[How to play sandbox with character and unlimited crafting? - Factorio Forums](https://forums.factorio.com/viewtopic.php?t=30018)

## There is no spoon
### Questions
* Best game settings?

### Need
* 2 red belts iron plate:
	* 120 miners, 2 red belts iron ore
	* 96 steel or electric furnaces (3*32)
* 2 red belts copper plate
* 0.5 yellow belt steel
	* 75 miners, 0.3 red belts iron ore
	* 60 steel or electric furnaces for iron (2*32)
	* 60 steel or electric furnaces for steel
* 1 red belt coal
	* 60 miners
* 2 belts from refinery -> main bus

## Train network using only vanilla circuits
The train network should carry red and green signals globally. The numbers used are standardized on train loads of common items.

* Red = want item
* Green = have item

So a red copper ore with 6 quantity means 6 trains of copper ore are wanted. This could be a station needing 6 trains of ore, or 6 stations each needing 1 train of ore

A green copper ore of 3 means 3 trains of copper ore are available

Laying Blueprints
* Fulfillment: hook both red and green global wires

Fulfillment Logic
* Constant: Add 1 of the item type requested
* Constant: How many items on train, output on cyan
* Math: divide crate count (and train count) by train size (cyan) to get number of train loads this stop has available
* Math cyan * -1, to cancel out the cyan signal when added
* Math: Yellow star + 0 to pass train loads through (without cyan)
* Decider: Disable when train is in station, by only passing train loads when T=0 (stopped train)
	* Output sent to global network on green
* Decider: Enable train stop. If train loads > 0 (green *), set S = 1 to enable train stop
* Math: Red signal from global network + 0, send to train stop to pass through to train, so it can wait until items are wanted
* Train stop
	* enable/disable when S>0
	* Send to train, how many items are wanted
	* Read stopped train, send train number on T
* Train
	* Load til full
	* Circuit: item > 0
* Light: lit with S > 0  (have train loads and no train in station)

Requester Logic
* Constant: Add item type requested, with how many you’d like to have in the chests
* Constant: How many items on train, output on cyan
* Math: divide crate count  by train size (cyan) to get number of train loads this stop wants
* Math cyan * -1, to cancel out the cyan signal when added
* Math: Yellow star + 0 to pass train loads through (without cyan)
* Decider: Disable when train is in station, by only passing train loads when T=0 (stopped train)
* Decider: Enable train stop. If train loads > 0 (green *), set S = 1 to enable train stop
* Decider:  If train loads > 0 (green *), send train load count out to global network on red wire
* Train Stop
	* enable/disable when S>0
	* Read train contents: sent to first math so train contents are included in crate count 
		* using red wire also sends S and T signals, but they turn negative and don’t get past the next math circuit
	* Read stopped train, send train number on T
* Train
	* Unload til empty
* Light: lit with S > 0  (want train loads and no train in station)

Depot Logic
* Math: Takes in green wire from global network. Add yellow * + 0. Without this circuit, the train calculates the path to the Fulfillment train stop before the stop gets enabled, so skips right past it. Basically adds a delay so stop is enabled before pathing.
* Train Stop:
	* Send to train: Sends available train loads to train

# Expensive mode
* https://forums.factorio.com/viewtopic.php?t=48961

# DeathRibbonworld
Trying to apply DeathWorld settings to a RibbonWorld

* Resources: All 100%
* Terrain: All 100%

Enemy
* Bases. Frequency 200%, size 200%
* Starting area: 75%
* Expansion: max distance 7, min group 5, max group 20, min cool 4 min, max cool 60mon
* Evolution: time 200, destroy 200, polution 12

Advanced: Absorption 50%, attack cost 50%, min damage trees 60, absorbed damaged tree 10, diffusion ratio 2%

Note: Chances of getting all resources are pretty slim, may need to be adjusted.

# Mods
Factorissimo2
* https://mods.factorio.com/mod/Factorissimo2/faq

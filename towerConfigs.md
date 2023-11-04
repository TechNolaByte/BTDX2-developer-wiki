# towerConfigs.json

## _Bases
These properties specify basic behavior of each tower

- **validTiles** <br>
	This property sets the tiles in which the tower can be placed.
	Must be specified as an array where: <br>
	1 - Land <br>
	2 - Water <br>

- **width/height** <br>
	This property affects how many tiles the tower occupies. Most towers are 2x2, but some larger ones may be 3x3.


## _Skins
These properties specify [???]

- **idleStart**
	[???]
- **idleEnd**
	[???]
- **idleRate**
	[???]
- **idleStartChance**
	[???]
- **idleInReload**
	[???]
- **attackStart**
	[???]
- **attackTriggers**
	[???]
- **attackEnd**
	[???]
- **attackOnAnimation**
	[???]
- **underlayIndex**
	[???]


## _Brains
These properties affect how different towers "think" and interact with the game. <br>
*These are the most important when it comes to towers, as they define nearly everything each tower does*

This should be written as a list of every possible tower/upgrade. Usually they'll be denoted with a number which signifies which upgrade of which path: <br>
Tower0 - no upgrades <br>
Tower1 - first base upgrade <br>
Tower2 - second base upgrade <br>
Tower3 - L3 <br>
Tower4 - L4 <br>
Tower5 - L5 <br>
Tower6 - M3 <br>
Tower7 - M4 <br>
Tower8 - M5 <br>
Tower9 - R3 <br>
Tower10 - R4 <br>
Tower11 - R5 <br>

- **name** <br>
	Self explanatory, this is the name of the tower (Dart, Tack, Boomerang)

- **description** <br>
	This is the description text shown when hovering over the tower card in the Shop

- **cost** <br>
	The cost for the tower/upgrade

- **range** <br>
	The range of a tower in pixels (1 tile = [???] pixels)

- **detectCamo** <br>
	A boolean value that determines if the tower has inherent camo detection

## Prime Attacks
A list of regular attacks each tower uses

- **rate** <br>
	How many times the attack is performed per frame (usually calculated with `1 / frames`)
	
- **F** <br>
		Tells the game which GML function to use when attacking

- **A** <br>
		These are the arguments that are passed to the function listed in `F`

- **P** <br>
		Tells the game what projectile to spawn

### Projectiles
Properties that define a projectile

- **objectID** <br>
	Specifies which GML object to use for the projectile: <br>
	[Here should be a list of possible objects and a very brief description]

- **sprite** <br>
	What sprite to use for the projectile

- **index** <br>
	[???]

- **Config** <br>
	Optional configuration for the projectile <br>
	- *rotationSpeed* - How many degrees to rotate the projectile sprite per frame
	- *path* - The path the projectile should make (specified as `pth_name` files)
	- *delay* - [???]
	- *fromAbility* - [???]
	- *range* - How many pixels the projectile can travel before its destroyed [???] Is this not redundant with ageLimit?
	- *maxDeviation* - [???]
	- *lightningPierce* - [???]
	- *moabShockDuration* - [???]
	- *moabShockRate* - [???]
	- *moabShockRange* - [???]
	- *moabShockPierce* - [???]
	- *killOnBlunt* - [???]
	- *immuneToBlunt* - [???]
	- *refreshPierceDelay* - [???]
	- *maxBounces* - Maximum number of times this projectile can bounce off walls/obstacles before it is destroyed
		##### Knockback/Stuns/Slows
	- *knockbackTime* - How many frames the knockback lasts [???]
	- *maxTimeVariation* - +/- the knockbackTime time, so the time a bloon/blimp is knocked back is any amount of frames between `knockbackTime - maxTimeVariation` and `knockbackTime + maxTimeVariation`
	- *knocksbackMOABS* - If this projectile can knock back blimps
	- *moabSlowdown* - An array of multipliers that are applied to each blimp's speed (lowest tier first) [???]
	- *stunRelief* - [???]
	- *bloonStun* - The amount of frames to stun a hit bloon
	- *moabStun* - An array of numbers detailing the amount of frames each tier of blimp is stunned for [???]
		##### Ricochet
	- *maxJumpDist* - How many pixels a projectile can jump
	- *count* - Number of times a projectile can jump before it is destroyed
	- *instantMode* - If the projectile can jump instantly

- **xscale/yscale** <br>
	[???]

- **scaleToWidth** <br>
	[???]
	
- **immuneToObstacles** <br>
	A boolean value that determines if the projectile can collide with obstacles

- **baseSpeed** <br>
	The amount of pixels the projectile travels each frame (1 tile = [???] pixels)

- **ageLimit** <br>
	The amount of frames that need to pass before this projectile is destroyed <br>
	*Putting a `-1` here will make the projectile never be destroyed by time*

- **repopDelay** <br>
	The amount of frames that need to pass before the same projectile can harm the same bloon

- **onlyCollideWithTarget** <br>
	A boolean that specifies whether or not the projectile should collide with any other bloons except the one it was directed at (mostly used for abilities such as MOAB Assassin)

- **payload** <br>
	This is a list of base properties of the projectile:
	- **pierce** - How many bloons the projectile can hit before being destroyed
	- [**damage_type**] - The damage type followed by the amount of damage it inflicts:
		- *sharp* - cannot damage lead
		- *omni* - can damage all bloon types
		- *explosive* - cannot damage black bloons
		- *knockback* - the amount of knockback the attack inflicts on bloons [???] (Not sure if the number is like amount of pixels or something)
		- *blimpKnockback* - the amount of knockback the attack inflicts on blimps [???] (Not sure if the number is like amount of pixels or something)
	- [**extra_damage_type**] - Extra damage this projectile does against specified bloon types:
		- extraBlimp - additional damage done to blimps
		- extraShell - additional damage done to ceramic bloons
		- extraShield - additional damage done to shields

- **contagions** <br>
	Specifies any effects the projectile applies to bloons/blimps:
	- *effect* - The effect it applies to bloons
		- "DOT" - damage over time
		- "property" - adds the property indicated by the `property` tag
	- *id* - The id of what the effect looks like [???]
		- "burning"
	- *property* - A property that can be added to a bloon
		- "marked" [???]
		- "deathMarked" [???]
	- *value* - Sets a property to true or false
	- *canStack* - Boolean value indicating if the effect can apply multiple times
	- *doesInherit* - Boolean value indicating if child bloons will inherit this effect
	- *duration* - Number of frames the effect lasts for
	- *frequency* - How often the effect "ticks" in frames
	- *amplitude* - [???]

- **emitOnCollision** <br>
	Specifies a new projectile that should be spawned when its parent collides with something

- **emitOnCustom** <br>
	Specifies a new projectile that should be spawned when [???]

- **emitOnDeath** <br>
	Specifies a new projectile that should be spawned when its parent is destroyed [???]
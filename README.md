# EZMount

## How to Use:

1. To use EZMount, first initialize it with this line of code:

```lua
local mount = require("EZMount")
```

2. Run one of the included functions to add a new custom mount. Arguments with a * are required, all other arguments can be replaced with nil

## newLivingMount

This is a function for replacing living entities like horses, camels, and pigs. Attempting to use this for non-living entities like boats and minecarts will cause errors.

The `newLivingMount` function has 9 arguments

1. A string for the id or name of the entity you want to replace*
2. The modelpart that contains all of the custom model's parts, must be a single group*
3. A modelpart, or a table of modelparts for the head of the entity, these part(s) will follow the up/down head rot of the entity
4. A modelpart, or a table of modelparts for the saddle of the entity, these part(s) will only be visible if the player is controlling the entity
5. A modelpart, or a table of modelparts for the saddle bags of the entity, these part(s) will only be visible if the entity has a chest
6. A modelpart of a table of modelparts for the armor of the entity, these part(s) will only be visible if the entity has armor on
7. A table containing textures associated with armor types, the script will match the armor parts texture with the armor being worn
   
Example (from the example avatar):
```lua
local armortex = {
    iron = textures["iron"],
    diamond = textures["diamond"],
    golden = textures["gold"],
    leather = textures["leather"]
}
```
8. A modelpart, or a table of modelparts for the passenger of the entity, these part(s) will only be visible if the entity has more than one passenger
9. A table assigning animations to specific animation states in the library
Example (including all available animations- this is from the example avatar):
```lua
local thing = animations.horse
local animlist = {
    still = thing.still,
    forward = thing.forward,
    backward = thing.backward,
    turnright = thing.turnright,
    turnleft = thing.turnleft,
    up = thing.jump,
    down = thing.down,
    rear = thing.rear,
    gallop = thing.gallop
}
```
Note: Not all entities can use all these animations, for examples, horses can't gallop (sprint), but camels can

Example (from the example avatar):
```lua
mount:newLivingMount("horse",models.horse,headcubes,saddlecubes,bagcubes,armorcubes,armortex,passengercubes,animlist)
```

## newObjectMount

This is a function for replacing non-living entities like boats and minecarts, attempting to use this for living entities may cause weirdness

The `newObjectMount` function has 4 arguments

1. A string for the id or name of the entity you want to replace*
2. The modelpart that contains all of the custom model's parts, must be a single group*
3. A modelpart, or a table of modelparts for the passenger of the entity, these part(s) will only be visible if the entity has more than one passenger
4. A table assigning animations to specific animation states in the library
Example (including all available animations- this is from the example avatar):
```lua
local boat = animations.boat
local boatList = {
    still = boat.still,
    forward = boat.forward,
    backward = boat.backward,
    turnright = boat.turnright,
    turnleft = boat.turnleft,
    up = boat.up,
    down = boat.down,
    rear = boat.rear,
    gallop = boat.gallop
}
```
Note: Not all entities can use all these animations, for examples, non-living entities probably can't rear or gallop

Example:
```lua
mount:newObjectMount("boat",models.boat,passengercubes,boatList)
```

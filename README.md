# Bomberman - Prototype

Kevin Attinger  
WS 2021/2022
OMB 7

Course: PRIMA
Docent: Prof. Dipl.-Ing. Jirka R. Dell'Oro-Friedl, HFU

[live](https://attinger.github.io/bomberman-game/) \
[source code](https://github.com/Attinger/bomberman-game) \
[design](https://github.com/Attinger/bomberman-game/design.pdf) 

## Description
I think everyone knows it, a attempt to rebuild the game Bomberman. 
You have to fight against three bots who are placing bombs around the map. Can you survive and destroy every possible block to win the game?

### Controls
**Movement:** W, A, S, D / Arrow-keys  (to move around)/ Space (to place a Bomb)

## Checklist for the final assignment
| Nr | Criterion            | Explanation                                                                                                              |
|---:|-------------------  |---------------------------------------------------------------------------------------------------------------------|
|  0 | Units and Positions |Every block has a width and height of 1; the Agent and the NPCs are half of that aswell as the bombs. Flames are 1 in every direction aswell.|
|  1 | Hierarchy           | A screenshot of the Hierarchy can be found in the Design Document (linked above).|
|  2 | Editor              | I used the Editor to create only one 1x1 Block which builds my base. Everything else is added via Code because the Mapsize can be modified by a user which i will explain on 8) External data.|
|  3 | Scriptcomponents  | My agent has a Scriptcomponent which controls things like movement or movement speed in gernal.|
|  4 | Extend            |Agent, Bomb, NPC, Flames inherit from f.Node to provide the functionality of adding components and graph placement|
|  5 | Sound             | My game has different Hit markers one for the Agent, one for the NPCs. Also if a bomb explodes it will return a Sound.|
|  6 | VUI               | The UI consits of a ,,Health - Bar'' for the Agent. It has an initial value of 2, if the Agent got hit 2 times by a Bomb and the Gamestate is equal to zero there will be a Gamerover screen popping up.|
|  7 | Event-System      | The eventsystem is used when flames from a bomb are created. It will fire a explode event which contains the flame position (i modified the event in the DataEvent.ts a bit), where i then can check if it has the same positons as a ,,Destroyable Block'' position, if true the block will remove itself. |
|  8 | External Data     | I implemented a Mapsize.JSON in this project. At the start of the game the user can selected between three different mapsizes. Depending on the user selection the correct size of the map will be fetched and will then do the following: scale the initiale block created in the fudge editor to the size, create walls, and destroyable blocks all depending on this selection.|
|  9 | Light             | A ambient light was placed on the floor node to provide a base luminance and aswell as a  directional light. |
|  A | Physics           | Rigidbody components: Agent, NPCs, Walls, Destroyable Blocks, Base. Forces on Agent. Collision Eventhandling on NPC's with Destroyable Blocks, Walls and Base. (also mentioned in the following - Statemachine|
|  C | State Machines    | My Statemachine controls the behaviour of my NPC by checking if they collide, and especially with who they collide, depending on that the statemachine transits into a different state and changes the behaviour of the NPC.|

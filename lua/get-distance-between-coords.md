# Problem
You have two coordinates; `playerPos` and `targetPos`, and you want to get the distance between the two

The simple solution is `GetDistanceBetweenCoords` or `Vdist`/`Vdist2`, but **DO NOT USE THESE, THEY ARE VERY SLOW**

In FiveM's Lua implementation, you can use `#(pos1 - pos2)` to get the distance between the two coordinates.

# Solution
```lua
-- coordinates
local playerPos = GetEntityCoords(PlayerPedId())
local targetPos = vector3(1151.5032958984, -1528.7556152344, 35.186698913574) -- St. Fiarce Hospital
-- ...
local distance = #(playerPos - targetPos)
-- ...
```

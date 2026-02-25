```squirrel title:
local stage = sq_GetGlobaludpModuleStage(); //得到模块
local dungeon = sq_GetDungeonByStage(stage); //得到副本模块
local dungeonIndex = sq_GetDuegonIndex(dungeon); //得到副本ID
local mapIndex = sq_GetMapIndex(stage); //得到mapID
```

```squirrel title:
local id = sq_GetObjectId(pTargetChr);//得到ID
local object = sq_GetObjectByObjectId(obj, id);//得到对象

local group = sq_GetGroup(targetObj);//组
local uniqueId = sq_GetUniqueId(targetObj);//唯一ID
local targetObj = sq_GetObject(obj, group, uniqueId);//得到对象
```
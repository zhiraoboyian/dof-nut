```squirrel title:
local ani = obj.getCurrentAnimation();
local radiusSize = sq_GetAniRealImageSize(ani, 0);

local boundBox = sq_GetAttackBoundRect(ani);
local bosXSize = sq_GetBoundingBoxXSize(boundBox);
local range = bosXSize;
```
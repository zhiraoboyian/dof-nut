
```squirrel title:得到对象管理器
local objectManager = obj.getObjectManager();
```


```squirrel title:得到map坐标
local xPos = objectManager.getFieldXPos(IMouse.GetXPos(), ENUM_DRAWLAYER_NORMAL);
local yPos = objectManager.getFieldYPos(IMouse.GetYPos(), 0, ENUM_DRAWLAYER_NORMAL);
local zPos = objectManager.getFieldZPos(IMouse.GetYPos(),目标y坐标, ENUM_DRAWLAYER_NORMAL);
```


```squirrel title:得到ui坐标
local uiXPos = mapXPos - (objectManager.getFieldXPos(mapXPos, ENUM_DRAWLAYER_NORMAL) - mapXPos);
local uiYPos = mapYPos - (objectManager.getFieldYPos(mapYPos, 0, ENUM_DRAWLAYER_NORMAL) - mapYPos);
```

```squirrel title:
obj.getXDistance(pChr); //对象类 得到x距离
obj.getYDistance(pChr); //对象类 得到y距离
```

```squirrel title:
local posX = CNRDObject.getAngleDistanceXPos(obj.getVar("pos").get_vector(0), angle, radius, ENUM_DIRECTION_RIGHT);
local posY = CNRDObject.getAngleDistanceYPos(obj.getVar("pos").get_vector(1), angle, radius, false);
```
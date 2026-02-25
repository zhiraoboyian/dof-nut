
```squirrel title:
//对象类
obj.getXPos(); //x坐标
obj.getYPos(); //y坐标
obj.getZPos(); //z坐标
```

```squirrel title:
//任意对象
sq_GetXPos(); //x坐标
sq_GetYPos(); //y坐标
sq_GetZPos(); //z坐标
local screenX = sq_GetScreenXPos(object); //位于屏幕x坐标
local screenY = sq_GetScreenYPos(object); //位于屏幕y坐标
```

```squirrel title:
//玩家
local mouseX = sq_GetMouseXPos(); //鼠标x坐标
local mouseY = sq_GetMouseYPos(); //鼠标y坐标
```

```squirrel title:
//对象类
pooledObj.setCurrentPos(x, y, z);
```

```squirrel title:
//任意对象
sq_SetCurrentPos(obj, x, y, z);
```

```squirrel title:
//设置单个x或y或z坐标
sq_setCurrentAxisPos(obj, 0, dstX); //设置当前x坐标
sq_setCurrentAxisPos(obj, 1, dstY); //设置当前y坐标
sq_setCurrentAxisPos(obj, 2, mz); //设置当前z坐标
```

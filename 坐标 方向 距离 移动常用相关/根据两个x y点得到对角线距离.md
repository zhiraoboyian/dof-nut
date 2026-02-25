```squirrel title:
local distance = sq_GetDistance(X, Y - Z, posX, posY - posZ, true); //得到对角线距离

sq_GetDistanceObject(obj, object, true); //得到距离对象
```

```squirrel title:
//开平方根得到距离
sqrt((x1 - x2) * 
	(x1 - x2) + 
	(y1 - y2) *
	(y1 - y2));
```
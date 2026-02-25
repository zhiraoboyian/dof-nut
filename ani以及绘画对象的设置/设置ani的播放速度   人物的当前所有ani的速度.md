
```squirrel title:
pAni.setSpeedRate(200.0); //速度率
obj.sq_SetAnimationSpeedRate(obj.sq_GetCurrentAni(), attackSpeedRate.tofloat()); //设置ani的速度率
```


```squirrel title:设置静态速度的信息
参数说明：
1.速度类型
2.速度类型
3.速度值
4.速度值
5.速度加成率
6.速度加成率一般为改最后面的两个参数可以调整速度
obj.sq_SetStaticSpeedInfo(SPEED_TYPE_ATTACK_SPEED, SPEED_TYPE_ATTACK_SPEED, SPEED_VALUE_DEFAULT, SPEED_VALUE_DEFAULT, 1.0, 1.0);



//按比例增加 不吃任何速度，固定增加速度 更改1.5的那个数值 就是增加50%的速度
obj.sq_SetStaticSpeedInfo(0, 0, 0, (1000 * 1.5).tointeger(), 0.0, 0.0); //设置固定速度
```



```squirrel title:
SPEED_TYPE_CONST <- 0
SPEED_TYPE_MOVE_SPEED <- 1 //移动速度
SPEED_TYPE_ATTACK_SPEED <- 2 //攻击速度
SPEED_TYPE_EXCEPT_WEAPON_ATTACK_SPEED <- 3 //除了攻击速度
SPEED_TYPE_CAST_SPEED <- 4 //施放速度
```

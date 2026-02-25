
```squirrel title:特效增加--删除--设置移动ptl
obj.sq_SetMoveParticle("Particle/ATWaterCannonMove.ptl", 0.0, 0.0); //设置移动的ptl 路径是特效的路径为父路径

obj.sq_RemoveMoveParticle(); //删除特效身上的移动ptl

//参数1：特效对象
//参数2：移动类型 0：x坐标  1：y坐标 2：z坐标
//参数3：速度值
sq_SetSpeedToMoveParticle(obj, 0, speed); //设置移动速度

obj.sq_AddObjectParticleCreater("Particle/ATWaterCannonTail.ptl"); //增加额外的ptl
obj.sq_SetObjectParticlePos(0, 1, 0); //设置创建ptl的x y z轴坐标
```


```squirrel title:增加一个以map为坐标的ptl
local particleCreater = obj.sq_var.GetparticleCreaterMap("ATWaterCannon", "PassiveObject/Character/Mage/Particle/ATWaterCannonTail.ptl", obj); //得到ptl
particleCreater.Restart(0); //重置
particleCreater.SetPos(x, y, z); //设置xyz
sq_AddParticleObject(obj, particleCreater); //增加ptl对象

```


```squirrel title:创建ptl--删除ptl
//参数1：路径
//参数2：对象
//参数3：x偏移（方向为右）
//参数4：y偏移
//参数5：z偏移
//参数6：是否跟随 参数2对象移动 bool值
//参数7：创建间隔
//参数8：最长存在时间
//参数9：最大创建次数
sq_CreateParticle("Character/Priest/Effect/Particle/ExcutionStonsLarge.ptl", obj, 180, 5, 250, true, 30, 0, 2); //创建ptl

sq_RemoveParticle("PassiveObject/Character/Mage/Particle/ATIceOrbDust.ptl", obj); //删除ptl

```



```squirrel title:未知没测试

sq_CreateParticleByGlobal(obj.getDustParticleType(LANDPARTICLE_MOVE), obj, x, 0, 0, true, 80, 120, 5);

sq_CreateParticleByGlobal(PARTICLE_CREATER_WATER_HIT_LIGHT, // ENUM_PARTICLE_CREATER

obj, // CNRDObject* master,
0, //int x,
- 1, //int y,
0, //int z,
true, //bool posistionFromMaster,
30, //int timeGap,
150, //int maxTime,

5); //int maxCount

```
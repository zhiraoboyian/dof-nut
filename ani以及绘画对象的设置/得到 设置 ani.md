```squirrel title:
//得到自定义ani
obj.sq_getCustomAni(CUSTOM_ANI_AVENGER_ATTACK_4_ROSARY); //复仇者
sq_GetCustomAni(obj, 57); //按道理是都可以用
local ani = obj.getCustomAnimation(0); //对象类
//得到当前ani
local ani = sq_GetCurrentAnimation(obj); //角色；特效；绘画对象
local ani = obj.getCurrentAnimation(); //角色；特效；绘画对象
local ani = obj.sq_GetCurrentAni(); //角色；
//得到默认ani
obj.getDefaultAnimation(); //对象类 得到默认ani
//判断是否是默认ani
obj.isCurrentAnimationDefault(); //对象类 判断是否是默认ani
//设置当前ani
obj.sq_SetCurrentAnimation(CUSTOM_ANI_CONCENTRATE_EX); //角色
setCurrentAnimationFromCutomIndex(obj, 0); //特效
obj.setCurrentAnimation(ani); //对象类

```
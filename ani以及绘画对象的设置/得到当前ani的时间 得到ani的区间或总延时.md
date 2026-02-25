```squirrel title:
local ani = obj.getCurrentAnimation();//角色；特效；绘画对象
//得到ani当前时间
local currentT = sq_GetCurrentTime(pAni);//ani得到当前时间
//得到ani延时
local delay = ani.getDelaySum(false);//ani延时总和
local delay = ani.getDelaySum(0, 2);//第几帧到第几帧总和
local delay = ani.getDelayBySpeedRate(1);//按照速度率
obj.sq_GetDelaySum();//得到当前的ani总延时 角色类对象
local startTime = sq_GetDelaySum(animation);//得到ani总延时
```
```squirrel title:
//得到自定义攻击信息
local attackInfo = sq_GetCustomAttackInfo(obj, 0);//角色；特效
//得到当前攻击信息
local attackInfo = sq_GetCurrentAttackInfo(obj);//角色；特效
//得到默认攻击信息
local attackInfo = sq_GetDefaultAttackInfo(obj);
//设置当前攻击信息
obj.sq_SetCurrentAttackInfo(CUSTOM_ATTACK_BLOODRIVENMULTIHIT);//角色
sq_SetCurrentAttackInfoFromCustomIndex(obj, 0);//特效
sq_SetCurrentAttackInfo(obj, attackInfo);//角色；特效
```
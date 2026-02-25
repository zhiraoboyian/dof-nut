```squirrel title:
local appendage = CNSquirrelAppendage.sq_AppendAppendage(obj, obj, SKILL_ATFIGHTER_FIREWORKS, false, "character/atfighter/fireworks/ap_fireworks.nut", true); //附加ap
local change_appendage = appendage.sq_GetCNChangeHp("changehp"); //得到hp
if (!change_appendage) change_appendage = appendage.sq_AddCNChangeHp("changehp", obj, obj, 0, 50000.0, 5000); //恢复设置

//参数1：name名称
//参数2：被附加对象
//参数3：附加对象
//参数4：0
//参数5：增加的hp值  浮点数
//参数6：恢复总时间

```
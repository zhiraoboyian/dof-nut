```squirrel title:
//增加可以看到图标的属性
local appendage = CNSquirrelAppendage.sq_AppendAppendage(obj, obj, SKILL_SUPPRESSINGFIRE, false, "character/gunner/suppressingfire/ap_suppressingfire.nut", false); //附加一个ap
local change_appendage = appendage.sq_getChangeStatus("changeStatus"); //ap的当前状态
if (!change_appendage) change_appendage = appendage.sq_AddChangeStatus("changeStatus", obj, obj, 500000, CHANGE_STATUS_TYPE_PHYSICAL_CRITICAL_HIT_RATE, false, 1000); //增加一个当前状态
//参数1：名
//参数2：对象
//参数3：对象
//参数4：有效时间
//参数5：增加的属性类型
//参数6：false为增加数值 true为增加百分比数值
//参数7：数值

```
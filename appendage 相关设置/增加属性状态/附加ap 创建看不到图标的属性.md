```squirrel title:
//增加看不到图标的属性 一般是被动技能会有一个技能图标，再用这个加上就不会有额外的icon出现 也会加属性
local change_appendage = appendage.sq_getChangeStatus("ele_atk_water"); //得到当前状态
if (!change_appendage) change_appendage = appendage.sq_AddChangeStatusAppendageID(obj, obj, 0, CHANGE_STATUS_TYPE_ELEMENT_ATTACK_WATER, false, registValue, APID_COMMON); //增加一个属性
if (change_appendage) {
	change_appendage.clearParameter();
	change_appendage.addParameter(CHANGE_STATUS_TYPE_ELEMENT_ATTACK_WATER, false, registValue.tofloat()); //在这里加上真实的属性
}
//参数1：增加的属性类型
//参数2：false为增加数值 true为增加百分比数值
//参数3：数值

```
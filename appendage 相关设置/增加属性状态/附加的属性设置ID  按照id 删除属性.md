#也可以删除所有属性
```squirrel title:
sq_RemoveChangeStatus(obj, APID_AT_MAGE_ELEMENT_SHIELD); //删除属性

local elementalType = obj.getThrowElement();
local upValue = sq_GetIntData(obj, SKILL_ELEMENTAL_SHIELD, 0);
local ap = sq_CreateChangeStatus(CHANGE_STATUS_TYPE_ELEMENT_TOLERANCE_FIRE + elementalType, false, upValue.tofloat(), 0);
if (ap) {
	ap.getAppendageInfo().setValidTime(validTime);
	ap.sq_Append(obj, obj, APID_AT_MAGE_ELEMENT_SHIELD, 0, null);
}
```
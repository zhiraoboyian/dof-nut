#测试效果不好 #使用原版的代码附加ap后会一直改变y坐标 #搞不明白到底有啥用

```squirrel title:
local appendage = CNSquirrelAppendage.sq_AppendAppendage(parentObj, obj, SKILL_FROZENLAND, false, "Appendage/Character/ap_common_suck.nut", false);
local suckVel = 200;
local radiusSize = obj.getVar("radius").get_vector(1);
local range = radiusSize * 2;
if (appendage) {
	appendage.sq_SetValidTime(2000);
	CNSquirrelAppendage.sq_Append(appendage, parentObj, obj);
	local auraAppendage = appendage.sq_getAuraMaster("frozenAura");
	if (!auraAppendage) auraAppendage = appendage.sq_AddAuraMaster("frozenAura", parentObj, obj, 1200, 18, 5, 0);
	auraAppendage.setAttractionInfo(suckVel, suckVel, range, 100);
}
```
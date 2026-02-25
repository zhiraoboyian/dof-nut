```squirrel title:
local appendage = CNSquirrelAppendage.sq_AppendAppendage(obj, obj, SKILL_ATFIGHTER_FIREWORKS, false, "character/atfighter/fireworks/ap_fireworks.nut", true); //附加ap

local hpmaxup_appendage = appendage.sq_getHpMaxUp("HpMaxUp"); //得到
if (!hpmaxup_appendage) //不存在
hpmaxup_appendage = appendage.sq_AddHpMaxUp("HpMaxUp", obj, obj, 0, 99999, 99999); //增加

//参数1：name名称
//参数2：被附加对象
//参数3：附加对象
//参数4：持续时间 写0则无限时间
//参数5：增加的hp值
//参数6：增加的mp值
```

```squirrel title:
数值需要通过运算后得到正确数值
local convert_rate = sq_GetAbilityConvertRate(obj, CONVERT_TABLE_TYPE_HP); //先得到转换率
local dooms_con_hp = dooms_hp.tofloat() * convert_rate.tofloat(); //得到正确的数值
```

```squirrel title:
//转换常量
CONVERT_TABLE_TYPE_DAMAGE <- 0 //  等嘐雖
CONVERT_TABLE_TYPE_DEFENSE <- 1 //  寞橫溘
CONVERT_TABLE_TYPE_HP <- 2 //  HP MAX
CONVERT_TABLE_TYPE_PHYSICAL_ATTACK <- 3 //  
CONVERT_TABLE_TYPE_PHYSICAL_DEFENSE <- 4 //  羹溘
CONVERT_TABLE_TYPE_MAGICAL_ATTACK <- 5 //  雖棟
CONVERT_TABLE_TYPE_MAGICAL_DEFENSE <- 6 //  薑褐溘
CONVERT_TABLE_TYPE_PHYSICAL_ABSOLUTE_DAMAGE <- 7 //  僭葬 瞰渠 等嘐雖
CONVERT_TABLE_TYPE_PHYSICAL_DAMAGE_REDUCE <- 8 //  僭葬 等嘐雖 爾薑
CONVERT_TABLE_TYPE_MAGICAL_ABSOLUTE_DAMAGE <- 9 //  葆徹 瞰渠 等嘐雖
CONVERT_TABLE_TYPE_MAGICAL_DAMAGE_REDUCE <- 10 //  葆徹 等嘐雖 爾薑
CONVERT_TABLE_TYPE_ACTIVESTATUS_DAMAGE_REDUCE <- 11 //  鼻鷓檜鼻 等嘐雖 爾薑.
CONVERT_TABLE_TYPE_MP <- 12 //  MP MAX
CONVERT_TABLE_TYPE_SKILL_POWER <- 13 //  蝶鑒 絮董等嘐雖
CONVERT_TABLE_TYPE_MAX <- 14
```
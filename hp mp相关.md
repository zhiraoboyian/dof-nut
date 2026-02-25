
#设置hp或者mp或者得到


```squirrel title:根据转换率得到转换后的实际hp值数值需要通过运算后得到正确数值
local convert_rate = sq_GetAbilityConvertRate(obj, CONVERT_TABLE_TYPE_HP); //先得到转换率
local dooms_con_hp = dooms_hp.tofloat() * convert_rate.tofloat(); //得到正确的数值
```


```squirrel title:转换常量
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


```squirrel title:得到设置hp mp
obj.getHpMax(); //活动类 得到hp上限
obj.getHp(); //活动类 得到当前hp
obj.setHp(0, null, true); //活动类 设置hp

obj.getMpMax(); //活动类 得到mp上限
obj.getMp(); // 活动类 得到当前mp
obj.sendSetMpPacket(obj.getMpMax()); //活动类 设置mp

sqrObj.sq_SendSetHpPacket(sqrObj.getHp() + hp, true, parentObj); //角色类 设置hp
sqrObj.sq_SendSetMpPacket(sqrObj.getHp() + hp, true, parentObj); //角色类 设置mp
```

​
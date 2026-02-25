#参数的介绍

```squirrel title:
//参数1：被附加ap者 参数2：附加的源对象
ap.sq_Append(obj, obj);//設置屬性的父對象

//参数1：被附加ap者 参数2：附加的源对象 参数3：设置ap的ID 不可重复附加
ap.sq_Append(obj, obj, APID_SKILL_LIGHT_ENCHANT_WEAPON);

//参数1：被附加ap者 参数2：附加的源对象 参数3：设置ap的ID 不可重复附加 参数4：可叠加次数 参数5：不明
ap.sq_Append(object, obj, APID_AT_MAGE_ELEMENT_SHIELD, 1, null);

//参数1：设置的ap  参数2：被附加ap者 参数3：附加的源对象 参数4：是否是buff
CNSquirrelAppendage.sq_Append(ap, obj, obj, true);

//参数1：设置的ap 参数2：被附加ap者 参数3：附加的源对象  参数4：设置apID 不可重复附加 参数5：是否是buff
CNSquirrelAppendage.sq_AppendAppendageID(ap, obj, obj, APID_SKILL_LIGHT_ENCHANT_WEAPON, false);


//是否是buff 改为false 则可以带过图 改为true 则不能带过图
```
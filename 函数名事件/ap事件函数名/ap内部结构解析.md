
```squirrel title:ap增加效果ani
function sq_AddEffect(appendage) {
	appendage.sq_AddEffectBack("Character/Common/Animation/BusterMode/buster_loop_back_normal.ani"); //背后
	appendage.sq_AddEffectFront("Character/Common/Animation/BusterMode/buster_loop_front_normal.ani"); //身前
}
```

```squirrel title:
appendage.sq_DeleteEffectFront(); //删除身前ani
appendage.sq_DeleteEffectBack(); //删除身后ani
local ani = appendage.sq_GetFrontAnimation(0); //得到身前的ani
local ani = appendage.sq_GetBackAnimation(0); //得到身后的ani
```


```squirrel title:是否是结束
local isEnd = sq_IsEnd(ani);
if (isEnd) {
	appendage.setValid(false); //销毁ap
}
```


```squirrel title:一开始时的设置
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onStart", "onStart_appendage_IceCrash")
}

function onStart_appendage_IceCrash(appendage) {
	if (!appendage) {
		return;
	}
	local parentObj = appendage.getParent();
	local sourceObj = appendage.getSource();

	if (!sourceObj || !parentObj) {
		appendage.setValid(false);
		return;
	}
}
```

​
```squirrel title:进入下一个map时
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onStartMap", "onStartMap_appendage_common_burster")
}

function onStartMap_appendage_common_burster(appendage) {
	if (!appendage) return;
	local obj = appendage.getParent();
	if (!obj) {
		appendage.setValid(false);
		return;
	}
	local validT = appendage.getAppendageInfo().getValidTime();
	local useTime = appendage.getTimer().Get();
	local remainT = validT - useTime;
	print(" remain validT:" + remainT);
	if (obj.isMyControlObject()) {
		if (remainT > 0) {
			sq_flashScreen(obj, 0, remainT, 300, 150, sq_RGB(0, 0, 0), GRAPHICEFFECT_NONE, ENUM_DRAWLAYER_BOTTOM);
		}
	}
}
```

```squirrel title:ap销毁结束时

function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onEnd", "onEnd_appendage_atmage_bodyeffect")
}
function onEnd_appendage_PushOut(appendage) {
	if (!appendage) {
		return;
	}
	local parentObj = appendage.getParent();

	if (!parentObj) {
		appendage.setValid(false);
		return;

	}
	if (parentObj.getState() == STATE_HOLD) {
		appendage.setValid(false);
		parentObj.sendStateOnlyPacket(STATE_STAND);
	}
}
```


```squirrel title:ap销毁结束时判断是否可结束
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("isEnd", "isEnd_appendage_atmage_bodyeffect")
}

function isEnd_appendage_avenger_awakening(appendage) {
	local T = appendage.getTimer().Get();
	if (appendage.sq_var.size_vector() != (I_AVENGER_AWAKENING_VALID + 1)) {
		return true;
	}
	local maxT = appendage.sq_var.get_vector(I_AVENGER_AWAKENING_TIME);
	local doomshp = appendage.sq_var.get_vector(I_DOOMS_HP); // 변신한 어벤져의 hp값
	if (T >= maxT || doomshp <= 0) { // 시간이 다 됐거나 둠스가디언 hp가 다 닳았다면.. 끝이다..
		//if(T >= maxT) {
		return true;
	}
	return false;
}

//在ap中进行判断才会运行 isEnd 函数
appendage.isEnd();
```


```squirrel title:有效时间结束时
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onVaildTimeEnd", "onVaildTimeEnd_appendage_atmage_elemental_change")
}
function onVaildTimeEnd_appendage_atmage_elemental_change(appendage) {
	if (!appendage)

	return;
	local parentObj = appendage.getParent();
	local sourceObj = appendage.getSource();

	if (!sourceObj || !parentObj) {
		appendage.setValid(false);
		return;
	}
	local mage = sq_ObjectToSQRCharacter(parentObj);
	if (mage)

	mage.setThrowElement(ENUM_ELEMENT_NONE);
	// 보호막형성 처리
	local appendage = CNSquirrelAppendage.sq_GetAppendage(mage, "Character/ATMage/MagicShield/ap_MagicShield.nut");
	if (appendage) setMagicShieldType(appendage, mage, mage.getThrowElement());
}
```


```squirrel title:被动
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("proc", "proc_appendage_atmage_diehard")
}

function proc_appendage_atmage_diehard(appendage) {
	if (!appendage) {
		return;
	}
	local parentObj = appendage.getParent();
	if (!parentObj) {
		appendage.setValid(false);
		return;
	}

}
```


```squirrel title:附加对象被攻击时
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onDamageParent", "onDamageParent_appendage_MagicShield")
}

function onDamageParent_appendage_MagicShield(appendage, attacker, boundingBox, isStuck)

{
	if (!appendage) {

		return;
	}
	local parentObj = appendage.getParent();
	parentObj = sq_GetCNRDObjectToSQRCharacter(parentObj);
	if (!parentObj) {
		appendage.setValid(false);
		return;
	}
}
```

​
```squirrel title:附加对象攻击时:这里也包括附加对象创建的特效
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onAttackParent", "onAttackParent_appendage_common_burster")
}
function onAttackParent_appendage_common_burster(appendage, realAttacker, damager, boundingBox, isStuck) {
	if (!appendage) {
		return;
	}
	// 버스터모드로 쳤다면..
	if (appendage.isValid()) {
		local centerX = sq_GetCenterXPos(boundingBox);
		local centerZ = sq_GetCenterZPos(boundingBox);
		local posY = damager.getYPos();
		local hitEffAni = sq_CreateAnimation("", "Character/Common/Animation/BusterMode/buster_hit_back_normal1.ani");
		local hitBackEffObj = sq_CreatePooledObject(hitEffAni, true);
		hitBackEffObj.setCurrentPos(centerX, posY - 1, centerZ);
		sq_AddObject(realAttacker, hitBackEffObj, OBJECTTYPE_DRAWONLY, false);
		local hitFrontEffAni = sq_CreateAnimation("", "Character/Common/Animation/BusterMode/buster_hit_front_dodge.ani");
		local hitFrontEffObj = sq_CreatePooledObject(hitFrontEffAni, true);
		hitFrontEffObj.setCurrentPos(centerX, posY + 1, centerZ);
		sq_AddObject(realAttacker, hitFrontEffObj, OBJECTTYPE_DRAWONLY, false);
	}
}
```



```squirrel title:附加对象设置hp时
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onSetHp", "onSetHp_appendage_avenger_awakening")
}
function onSetHp_appendage_avenger_awakening(appendage, hp, attacker) {
	local obj = appendage.getParent();
	if (appendage.sq_var.size_vector() != (I_AVENGER_AWAKENING_VALID + 1)) {
		return -1;
	}
	if (attacker && obj && obj.isEnemy(attacker)) { // 적에 의한
		local org_hp = hp;
		if (org_hp <= 0) {
			org_hp = 1;
			appendage.sq_var.set_vector(I_DOOMS_HP, 0);
		}
		return org_hp;
	}
	return -1;
}
```


```squirrel title:设置被攻击的伤害率
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("getImmuneTypeDamageRate", "getImmuneTypeDamageRate_appendage_MagicShield")
}

function getImmuneTypeDamageRate_appendage_MagicShield(appendage, damageRate, attacker)

{
	if (!appendage) return damageRate;
	local parentObj = appendage.getParent();
	parentObj = sq_GetCNRDObjectToSQRCharacter(parentObj);
	if (!parentObj) {
		appendage.setValid(false);
		return damageRate;
	}
	local var = appendage.getVar();
	if (!var)

	return damageRate;
	local type = parentObj.getThrowElement();
	// 수속성 : 데미지 일정 횟수 완전 방어
	if (type == ENUM_ELEMENT_WATER)

	return 0;
	local type = parentObj.getThrowElement();
	// 레벨인포로 데미지율이 조정됨.
	local skill_level = parentObj.sq_GetSkillLevel(SKILL_MAGIC_SHIELD);

	local decreaseRate = parentObj.sq_GetLevelData(SKILL_MAGIC_SHIELD, 1, skill_level); // 1. 데미지 감소율(%)
	damageRate = damageRate - decreaseRate;
	return damageRate;
}
```


```squirrel title:源对象的ani-key-flag标签
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onSourceKeyFrameFlag", "onSourceKeyFrameFlag_appendage_mage_electricrabbit");
}

function onSourceKeyFrameFlag_appendage_mage_electricrabbit(appendage, flagIndex) {
	if (!appendage) return;

	local obj = appendage.getParent();
	if (obj) {
		obj = sq_GetCNRDObjectToSQRCharacter(obj);
		obj.getVar("debugnew2").push_vector(flagIndex);
		obj.getVar("debugnew2").push_vector(attacker.getXPos());
	}
}
```


```squirrel title:附加对象创建的对象被破坏时
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onDestroyObject", "onDestroyObject_appendage_grab_icemagic")
}

function onDestroyObject_appendage_grab_icemagic(appendage, destroyObj) {
	if (!appendage) return true;
	if (destroyObj == appendage.sq_GetSourceChrTarget()) {
		appendage.setValid(false);
	}
	return true;
}
```


```squirrel title:可以画出附加对象图层的动画ani
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("drawAppend", "drawAppend_appendage_MagicShield")
}
//参数x y为我自己的位置
//isOver参数为true画身前 false画身后
//isFlip判断是否翻转
function drawAppend_appendage_MagicShield(appendage, isOver, x, y, isFlip) {
	if (!appendage) {
		return;
	}
	local obj = appendage.getParent();
	if (!obj) {
		appendage.setValid(false);
		return;
	}
	local var = appendage.getVar();
	local backAni = var.getAnimation(VAR_MAGIC_SHIELD_BACK_ANI);
	local frontAni = var.getAnimation(VAR_MAGIC_SHIELD_FRONT_ANI);

	if (frontAni && isOver) {
		sq_AnimationProc(frontAni);

		sq_drawCurrentFrame(frontAni, x, y, isFlip);
	}
	else if (backAni && !isOver) {
		sq_AnimationProc(backAni);
		sq_drawCurrentFrame(backAni, x, y, isFlip);
	}
	//自定义ani
	local Ani = var.GetAnimationMap("flashcutbg_01", "character/swordman/effect/animation/flashcut/flashcutbg_01.ani");

	sq_AnimationProc(Ani);
	sq_drawCurrentFrame(Ani, 400, y, isFlip);
}
```


```squirrel title:画附加对象的ui图层是否继续画
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("isDrawAppend", "isDrawAppend_appendage_atmage_tundra_cs")
}
function isDrawAppend_appendage_atmage_tundra_cs(appendage) {
	local obj = appendage.getParent();
	if (!obj) {
		appendage.setValid(false);
		return false;
	}
	local mode = appendage.getVar("mode").get_vector(0);
	if (sq_IsValidActiveStatus(obj, ACTIVESTATUS_FREEZE) || mode == MODE_FREEZE) {
		return false;
	}
	return true;
}
```



```squirrel title:ap改变状态时#如果设置相同状态则不会运行#只有在设置不同状态时才会运行
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onChangeState", "onChangeState_execution");
}
function onChangeState_execution(appendage, oldState, newState, datas) {
	if (!appendage) return;
	appendage.sq_var.setBool(EXC_VAR_MOVE_ACTIVE, true);
	appendage.sq_var.setInt(EXC_VAR_CURRENT_STATE, newState); //현재 스테이트 : 부모의 키프레임값
	// 잡기 불가적은 뒤로 던지기 전에 풀어준다.
	if (newState >= 7 && !isGrabableParent(appendage)) {
		appendage.setValid(false);
		return;
	}
	setNewState_execution(appendage, oldState, newState, false);
}

//ap 发送状态
appendage.setState(flagIndex, sq_GetGlobalIntVector());​
```



```squirrel title:得到附加对象被攻击时的伤害数值#就是获取被攻击时打了多少伤害但是组队会不运行
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("onApplyHpDamage", "onApplyHpDamage_appendage_atmage_tundra_cs")
}
function onApplyHpDamage_appendage_atmage_tundra_cs(appendage, newHpDamage, attacker) {
	local obj = appendage.getParent();
	if (!obj) return newHpDamage;
	local damage = newHpDamage;
	if (sq_IsValidActiveStatus(obj, ACTIVESTATUS_FREEZE)) {

		local frozenAddDamageRate = appendage.getVar("skl").get_vector(4); // 4.얼어있는 적 추가 데미지
		local addDamage = newHpDamage.tofloat() * frozenAddDamageRate.tofloat() / 100.0;
		print(" addDamage:" + addDamage);
		damage = damage + addDamage.tointeger();
	}
	return damage;
}
```


```squirrel title:未知#hearthings
function sq_AddFunctionName(appendage) {
	//appendage.sq_AddFunctionName("hearthings", "proc_appendage_priest_scythe_mastery")
}
```


```squirrel title:准备画
function sq_AddFunctionName(appendage) {
	appendage.sq_AddFunctionName("prepareDraw", "prepareDraw_appendage_atmage_darknessmantle_effect")
}

function prepareDraw_appendage_atmage_darknessmantle_effect(appendage) {
	if (!appendage) {
		return;
	}
	local obj = appendage.getParent();
}
```
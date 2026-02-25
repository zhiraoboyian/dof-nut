```squirrel title:
function procSkill_ATMage(obj) {
	procSkill_IceRoad(obj);
}

function procSkill_IceRoad(obj) {
	local appendage = obj.GetSquirrelAppendage("Character/ATMage/IceRoad/ap_ATMage_IceRoad.nut");
	if (appendage) {
		local isvalid = appendage.isValid();
		if (isvalid) {
			local currentT = appendage.getTimer().Get();
			local t = appendage.sq_var.get_timer_vector(0);
			local t2 = appendage.sq_var.get_timer_vector(1);
			if (t2.isOnEvent(currentT) == true) {
				local skill = sq_GetSkill(obj, SKILL_ICEROAD);
				if (skill) {
					local skill_level = obj.sq_GetSkillLevel(SKILL_ICEROAD);
					local spendMp = obj.sq_GetLevelData(SKILL_ICEROAD, SKL_LV_0, skill_level);
					if (spendMp > obj.getMp()) {
						appendage.setValid(false);
						skill.setSealActiveFunction(true);
						return;
					}
					else {

						print(" spendMp:" + spendMp);
						obj.sendSetMpPacket(obj.getMp() - spendMp);
					}
				}
			}
			if (t.getEventTerm() == -1) return;
			if (t.isOnEvent(currentT) == true) {
				if (obj.isMyControlObject()) {
					if (obj.getZPos() == 0) {
						local skill_level = sq_GetSkillLevel(obj, SKILL_ICEROAD);
						local change_time = sq_GetLevelData(obj, SKILL_ICEROAD, SKL_LV_1, skill_level);
						local rate = sq_GetLevelData(obj, SKILL_ICEROAD, SKL_LV_3, skill_level);
						local movSpd = sq_GetLevelData(obj, SKILL_ICEROAD, SKL_LV_2, skill_level);
						sq_BinaryStartWrite();
						sq_BinaryWriteDword(change_time);

						sq_BinaryWriteDword(rate);
						sq_BinaryWriteDword(movSpd);

						local skillLevel = sq_GetSkillLevel(obj, SKILL_ICEROAD_EX);
						sq_BinaryWriteWord(skillLevel);
						if (skillLevel > 0) {
							local prob = sq_GetLevelData(obj, SKILL_ICEROAD_EX, 4, skillLevel) / 10.0;
							local asLevel = sq_GetLevelData(obj, SKILL_ICEROAD_EX, 5, skillLevel);
							local validTime = sq_GetLevelData(obj, SKILL_ICEROAD_EX, 6, skillLevel);
							sq_BinaryWriteFloat(prob.tofloat());

							sq_BinaryWriteWord(asLevel);
							sq_BinaryWriteDword(validTime);
						}
						sq_SendCreatePassiveObjectPacket(obj, 24243, 0, 0, 0, 0, obj.getDirection());
					}
				}
			}
		}
	}
}
```
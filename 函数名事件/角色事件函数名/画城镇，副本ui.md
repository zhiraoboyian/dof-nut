#城镇中和副本中都可以画 #图层较低
```squirrel title:
function drawMainCustomUI_CreatorMage(obj) {
	if (!obj) return;
	local sq_var = obj.getVar();

	local hud_creator_b_gauge = sq_var.GetAnimationMap("hud_creator_b_gauge", "Character/Mage/CreatorAnimation/ui/hud_creator_b_gauge.ani");
	local hud_creator_b_select = sq_var.GetAnimationMap("hud_creator_b_select", "Character/Mage/CreatorAnimation/ui/hud_creator_b_select.ani");
	local skill_ui_index = 0;
	local x = 626;
	local y = 588;
	local offset = 36;

	local hudCreatorAni = sq_var.GetAnimationMap("hud_creator_back", "Character/Mage/CreatorAnimation/ui/hud_creator_back.ani");
	sq_DrawSpecificFrame(hudCreatorAni, x, y, false, 0, false, 1.0);

	if (!IsInBattleCreator(obj)) {
		local isEnable = isEnableCreatorBattleInUI();
		if (!isEnable) {
			unLockMouse(obj);
		}

	}

	if (getCreatorSkillStateSkillIndex(obj) != -1) {
		local type = getCreatorSkillStateSkillIndex(obj);
		local skillmgr = obj.getSkillManager();
		local slot = -1;
		if (skillmgr) {
			local index = getTypeSkillIndex(obj, type);
			slot = skillmgr.getSlotindex(index);
		}
		if (slot != -1) {

			sq_AnimationProc(hud_creator_b_select);
			sq_drawCurrentFrame(hud_creator_b_select, x + (slot * offset), y, false);
		}
	}

	local hud_creator_b_gauge = sq_var.GetAnimationMap("hud_creator_b_gauge", "Character/Mage/CreatorAnimation/ui/hud_creator_b_gauge.ani");

	local skillmgr = obj.getSkillManager();
	if (!skillmgr) return;
	for (local i = CREATOR_TYPE_FLAME; i < CREATOR_TYPE_MAX; i++) {
		local slot = -1;
		if (skillmgr) {
			local index = getTypeSkillIndex(obj, i);
			slot = skillmgr.getSlotindex(index);
		}
		if (slot != -1) {
			local appendage = getCreatorMageAppendageByType(obj, i);
			if (appendage) {
				local gaugeValue = 0;
				local max_gaugeValue = 0;
				max_gaugeValue = appendage.sq_var.get_vector(I_MAX_COUNT);
				gaugeValue = appendage.sq_var.get_vector(I_REMAIN_COUNT);

				local rate = gaugeValue.tofloat() / max_gaugeValue.tofloat();
				local rgb = getCreatorTypeColor(obj, i);
				local alpha = sq_ALPHA(255);
				hud_creator_b_gauge.setImageRate(rate, 1.0);
				local gaugePosX = x - 87;
				sq_DrawSpecificFrameEffect_SIMPLE(hud_creator_b_gauge, gaugePosX + (slot * offset), y, 0, rgb, alpha, true);
			}
		}
	}
}
```
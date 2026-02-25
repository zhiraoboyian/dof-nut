#只能在副本中进行画ui
```squirrel title:
function drawCustomUI_CreatorMage(obj) {

	if (!obj) return;
	if (!IsInBattleCreator(obj)) {
		return;
	}

	local isLock = sq_IsClipCursor();
	if (!isLock) {
		if (!sq_IsVisibleCursor()) {
			sq_SetVisibleCursor(true);
		}
		return;
	}
	if (sq_IsVisibleCursor()) {
		sq_SetVisibleCursor(false);
	}
	local ani = obj.getVar().GetAnimationMap("NORMAL", "Character/Mage/Effect/Animation/CreatorMagicSphere/normal.ani");
	local usingSkillIndex = getCreatorSkillStateSkillIndex(obj);
	if (usingSkillIndex == CREATOR_TYPE_DISTURB) {
		local stage = sq_GetObjectManagerStage(obj);
		if (!stage) return;
		local control = stage.getMainControl();
		if (control.IsRBDown()) {
			ani = obj.getVar().GetAnimationMap("THROW", "Character/Mage/Effect/Animation/CreatorMagicSphere/draw_cursor.ani");
		}
		else {
			ani = obj.getVar().GetAnimationMap("BLOCK", "Character/Mage/Effect/Animation/CreatorMagicSphere/block.ani");
		}
	}
	else if (usingSkillIndex == CREATOR_TYPE_GUARDIAN) {
		ani = obj.getVar().GetAnimationMap("GUARD", "Character/Mage/Effect/Animation/CreatorMagicSphere/guard.ani");
	}
	else if (usingSkillIndex == CREATOR_TYPE_ICE) {
		ani = obj.getVar().GetAnimationMap("ICE", "Character/Mage/Effect/Animation/CreatorMagicSphere/icesphere.ani");
	}
	else if (usingSkillIndex == CREATOR_TYPE_FLAME) {
		ani = obj.getVar().GetAnimationMap("FIRE",

		"Character/Mage/Effect/Animation/CreatorMagicSphere/firesphere.ani");
	}
	else if (usingSkillIndex == CREATOR_TYPE_WIND) {
		ani = obj.getVar().GetAnimationMap("WIND", "Character/Mage/Effect/Animation/CreatorMagicSphere/wind.ani");
	}
	local state = obj.getState();
	if (state == STATE_ICESHIELD) {
		ani = obj.getVar().GetAnimationMap("SHIELD", "Character/Mage/Effect/Animation/CreatorMagicSphere/shield_cursor_dodge.ani");
	}
	else if (state == STATE_FIREHURRICANE) {
		ani = obj.getVar().GetAnimationMap("HURRICANE", "Character/Mage/Effect/Animation/CreatorMagicSphere/hurricane_cursor.ani");
	}
	if (ani) {
		local posX = IMouse.GetXPos();
		local posY = IMouse.GetYPos();
		sq_AnimationProc(ani);
		sq_drawCurrentFrame(ani, posX, posY, false);
	}

}
```
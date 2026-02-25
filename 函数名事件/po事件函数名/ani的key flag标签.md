```squirrel title:
function onKeyFrameFlag_po_ATPieceOfIceCore(obj, flagIndex) {
	if (!obj) return false;
	if (flagIndex == 1) {
		sq_SetMyShake(obj, 3, 100);
	}
	if (flagIndex == 2) {

		obj.sendStateOnlyPacket(PIECE_OF_ICE_CORE_STATE_END);
	}
	return true;
}

//返回值应用：返回true 运行成功， 返回false 运行不成功 会多运行几次

```
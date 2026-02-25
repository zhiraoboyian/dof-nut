```squirrel title:
function onEndCurrentAni_po_ATConcentrateExpSmall(obj) {
	if (!obj) return;
	if (obj.isMyControlObject()) {
		sq_SendDestroyPacketPassiveObject(obj);
	}
}
```
```squirrel title:

function onEndMap_ElementalRain(obj) {
	if (obj.sq_IsMyControlObject()) {

		local ballCount = obj.getMyPassiveObjectCount(24233);
		printc("ballCount" + ballCount);
		for (local i = 0; i < ballCount; ++i) {
			local magicBall = obj.getMyPassiveObject(24233, i)
			if (!magicBall) continue;
			if (obj.sq_IsMyControlObject()) {
				print("onEndMap_ElementalRain");
				sq_SendDestroyPacketPassiveObject(magicBall);
			}
		}
	}
}
```
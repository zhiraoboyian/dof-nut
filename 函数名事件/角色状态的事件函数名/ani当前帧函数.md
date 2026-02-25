#缔造者
```squirrel title:
function onEnterFrame_FireHurricane(obj, frameIndex) {
	if (!obj) return;
	local t = obj.getVar("state").get_ct_vector(0);
	local time = 0;
	if (t) time = t.Get();
	local ani = sq_GetCurrentAnimation(obj);
	if (!ani) return;
}
```
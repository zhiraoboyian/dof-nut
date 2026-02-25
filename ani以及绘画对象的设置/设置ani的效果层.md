#在原图片图层上再增加一个图型样式


```squirrel title:
local effectType = GRAPHICEFFECT_DODGE; //图形效果类型

local rgb = sq_RGB(0, 90, 255); //rgb颜色值

local effectT = 600;
local startT = 200;
local endT = 50;
local targetV = endT;
local al = sq_GetUniformVelocity(startT, targetV, appendage.getTimer().Get(), effectT);
local alpha = sq_ALPHA(al); //获得透明度
//设置效果层  最后一个参数是 所有层ani是否也更改
pAni.setEffectLayer(true, effectType, true, rgb, alpha, true, false);
```

```squirrel title:
GRAPHICEFFECT_NONE <- 0 //  橈擠
GRAPHICEFFECT_DODGE <- 1 //  游雖
GRAPHICEFFECT_LINEARDODGE <- 2 //  葬棲橫 游雖
GRAPHICEFFECT_DARK <- 3 //  棻觼
GRAPHICEFFECT_XOR <- 4 //  XOR
GRAPHICEFFECT_MONOCHROME <- 5 //  欽儀
GRAPHICEFFECT_SPACE_DISTORT <- 6 //  奢除諼堊
GRAPHICEFFECT_MAX <- 7
```

```squirrel title:
//以下是我自己实操，巡回更改颜色值
local pAni = parentObj.getCurrentAnimation(); //得到当前ani
if (pAni) {
	local currentT = appendage.getTimer().Get(); //当前时间
	local fireT = 350; //总时间
	if (currentT / fireT % 2 == 1) {
		currentT = fireT - currentT % fireT; //再次计算轮回时间
	}
	else currentT = currentT % fireT; //轮回当前时间
	local al = sq_GetUniformVelocity(10, 100, currentT, fireT); //计算透明度
	local alpha = sq_ALPHA(al); //得到透明度
	local rgb = sq_RGB(255, 0, 0); //rgb 红色
	pAni.setEffectLayer(true, GRAPHICEFFECT_LINEARDODGE, true, rgb, alpha, true, false); //设置效果层
	//得到层ani 范围
	local size = sq_AniLayerListSize(pAni);
	for (local i = 0; i < size; i++) {
		local aniL = sq_getAniLayerListObject(pAni, i); //得到层ani
		if (aniL) {
			local effect = aniL.GetCurrentFrame().GetGraphicEffect(); //得到ani当前帧的效果
			if (effect != GRAPHICEFFECT_LINEARDODGE) //不是线性减淡 那么就改变颜色
			aniL.setEffectLayer(true, GRAPHICEFFECT_LINEARDODGE, true, rgb, alpha, true, false);
		}
	}
}
```
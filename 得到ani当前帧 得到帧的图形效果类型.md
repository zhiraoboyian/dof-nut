#例如判断线性减淡等等

```squirrel title:
local frame = ani.GetCurrentFrame();//得到当前帧

local effect = aniL.GetCurrentFrame().GetGraphicEffect();//得到图形效果


GRAPHICEFFECT_NONE <- 0 		  //  橈擠
GRAPHICEFFECT_DODGE <- 1 		  //  游雖
GRAPHICEFFECT_LINEARDODGE <- 2 		  //  葬棲橫 游雖
GRAPHICEFFECT_DARK <- 3 		  //  棻觼
GRAPHICEFFECT_XOR <- 4 		  //  XOR
GRAPHICEFFECT_MONOCHROME <- 5 		  //  欽儀
GRAPHICEFFECT_SPACE_DISTORT <- 6 		  //  奢除諼堊
GRAPHICEFFECT_MAX <- 7 
```
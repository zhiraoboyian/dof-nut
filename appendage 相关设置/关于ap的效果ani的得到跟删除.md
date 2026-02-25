```squirrel title:
appendage.sq_DeleteEffectFront(); //删除身前ani
appendage.sq_DeleteEffectBack(); //删除身后ani
appendage.sq_AddEffectBack("Character/Common/Animation/BusterMode/buster_loop_back_normal.ani"); //背后        appendage.sq_AddEffectFront("Character/Common/Animation/BusterMode/buster_loop_front_normal.ani");//身前

local ani = appendage.sq_GetFrontAnimation(0); //得到身前的ani
local ani = appendage.sq_GetBackAnimation(0); //得到身后的ani
//是否是结束
local isEnd = sq_IsEnd(ani);
if (isEnd) {
	appendage.setValid(false); //销毁ap
}
```
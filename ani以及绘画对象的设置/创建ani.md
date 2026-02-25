```squirrel title:
local ani = sq_CreateAnimation("","");//创建ani
参数1： 参数2：都是路径

//根据角色类型，来取决于路径
obj.sq_CreateCNRDAnimation("Effect/Animation/ATElementalRain/Cast/1_under_dodge.ani")

local ani = obj.getVar().GetAnimationMap("Disaster1", "Character/Priest/Animation/disasterEx/Disaster1.ani");
```
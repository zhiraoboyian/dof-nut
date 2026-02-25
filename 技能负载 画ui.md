```squirrel title:
//增加技能负载
obj.sq_AddSkillLoad(SKILL_ATGUNNER_HS12, 50, 1, 500);//技能编号，img序号，可以使用几次，冷却时间
//删除技能负载
obj.sq_RemoveSkillLoad(SKILL_ATGUNNER_HS12);//技能编号

//得到技能负载
local loadSlot = obj.sq_GetSkillLoad(SKILL_ATGUNNER_HS12);
//判断是否在冷却中
loadSlot.isCooling();
//使用几次
loadSlot.use(1);
//得到剩余装载数
loadSlot.getRemainLoadNumber();
//开始冷却
loadSlot.setStartCool();
//得到总冷却时间
loadSlot.getEndCoolTime();
//得到现在的冷却时间、
loadSlot.getCurrentCoolTime();
//得到icon ID
loadSlot.getInconIndex();

//icon图标路径 //台服最多不能超过50
sprite/character/common/customui/icon.img
```
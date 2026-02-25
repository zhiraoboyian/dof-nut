#ani的子ani

```squirrel title:
currentAni.addLayerAnimation(6,sq_CreateAnimation("","PassiveObject/Character/Mage/Animation/ATLightningWall/7_el-p1_dodge_1.ani"),true);//增加层ani

pAni.removeLayerAnimation(backlight_dodge);//删除层ani

local size = sq_AniLayerListSize(pAni);//得到ani层的范围

local pAniL = sq_getAniLayerListObject(pAni, i);//得到层ani
```
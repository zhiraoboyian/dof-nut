
#函数drawCustomUI

```squirrel title:
//普通画动图ui
sq_AnimationProc(ani);
sq_drawCurrentFrame(ani, x, y, false);
```

```squirrel title:
//可以增加rgb 或者透明度
sq_AnimationProc(gauge_normal_flash);
sq_drawCurrentFrameEffect_SIMPLE(gauge_normal_flash, x, y, rgb, alpha);
```

```squirrel title:
//画的固定帧 坐标是取的绝对屏幕坐标
sq_DrawSpecificFrame(hudCreatorAni, x, y, false, 0, false, 1.0);
```

```squirrel title:
//rgba
sq_DrawSpecificFrameEffect_SIMPLE(hud_creator_b_gauge, gaugePosX + (slot * offset), y, 0, rgb, alpha, true);
```

```squirrel title:
//没用过这个 原版是在特效中的被动 但是被注释掉了
sq_drawCurrentFrameEffectColor(ani, GRAPHICEFFECT_MONOCHROME, true, sq_RGB(255, 255, 255), sq_ALPHA(255));
```

```squirrel title:
//画出预设弹窗文字
sq_drawToolTip(x - 35, y - 13, sq_RGB(255, 255, 255), 0, 1, 29003, 0, 260, true);
```
```squirrel title:
//设置效果层;参数4：到达指定颜色需要的时间 参数5：消失的多少时间 参数6：附加多长时间
sq_EffectLayerAppendage(damager,sq_RGB(0,144,255),150,0,0,240);
sq_EffectLayerAppendageOnlyBody(obj, sq_RGB(255,255,255), 255, 0, 0, 320);

sq_SetBodyEffect(obj, obj, true, sq_RGB(255, 255, 255), 0, 80, 0, sq_ALPHA(255));
```
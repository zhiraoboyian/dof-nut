

```squirrel title:
//設置攻擊異常狀態；攻击信息，，异常类型，概率，等级，时间，伤害
sq_SetChangeStatusIntoAttackInfo(attackInfo, 0, ACTIVESTATUS_BLEEDING, bleedingrate, bleedinglevel, bleedingtime, bleedingdamage);
```

```squirrel title:异常状态常量
ACTIVESTATUS_SLOW <- 0 //  减速
ACTIVESTATUS_FREEZE <- 1 //  冰冻
ACTIVESTATUS_POISON <- 2 //  中毒
ACTIVESTATUS_STUN <- 3 //  眩晕
ACTIVESTATUS_CURSE <- 4 //  诅咒
ACTIVESTATUS_BLIND <- 5 //  失明
ACTIVESTATUS_LIGHTNING <- 6 //  感电
ACTIVESTATUS_STONE <- 7 //  石化
ACTIVESTATUS_SLEEP <- 8 //  睡眠
ACTIVESTATUS_BURN <- 9 //  燃烧
ACTIVESTATUS_WEAPON_BREAK <- 10 //  武器破甲
ACTIVESTATUS_BLEEDING <- 11 //  出血
ACTIVESTATUS_HASTE <- 12 //  加速
ACTIVESTATUS_BLESS <- 13 //  祝福
ACTIVESTATUS_ELEMENT <- 14 //  엘레먼트
ACTIVESTATUS_CONFUSE <- 15 //  混乱
ACTIVESTATUS_HOLD <- 16 //  束缚
ACTIVESTATUS_ARMOR_BREAK <- 17 //  护甲破甲
ACTIVESTATUS_MAX <- 18
```
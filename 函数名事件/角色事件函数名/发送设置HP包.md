```squirrel title:
function sendSetHpPacket_ATMage(obj, hp, sendInstant) {
	if (CNSquirrelAppendage.sq_IsAppendAppendage(obj, "Character/ATMage/DieHard/ap_ATMage_DieHardSlowHeal.nut")) {
		if (obj.getHp() < hp) {

			return false;
		}
	}

	return true;
}
```
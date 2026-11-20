# Onlayn reytingni ulash (bir marta, ~5 daqiqa)

Ilova o'yinchilar ballarini bepul Firebase Realtime Database'da saqlaydi.
Ilovani yuklagan hamma odam bir xil reytingni ko'radi, "hozir o'ynayotganlar" ham chiqadi.

1. https://console.firebase.google.com ga Google akkaunt bilan kiring → **Add project** → nom: `karra-jadval` → Google Analytics ni o'chiring → **Create project**.
2. Chap menyuda **Build → Realtime Database → Create Database**. Joylashuvni tanlang (istalgan), **Start in locked mode** → **Enable**.
3. **Rules** bo'limiga o'ting, ichidagini o'chirib, `firebase-rules.json` faylining mazmunini joylang → **Publish**.
4. **Data** bo'limining tepasidagi manzilni nusxalang. U shunga o'xshaydi:
   `https://karra-jadval-default-rtdb.firebaseio.com` yoki `https://karra-jadval-default-rtdb.europe-west1.firebasedatabase.app`
5. GitHub'da `www/config.js` faylini oching (qalamcha belgisi), `window.KARRA_DB_URL = "..."` ichiga manzilni qo'ying → **Commit changes**.
   APK avtomatik qayta yig'iladi (Releases bo'limida yangi versiya chiqadi).

## Nimalar saqlanadi
Faqat ota-ona ruxsat bergan o'yinchilar: ism (familiyasiz), rasm, ballar, o'yinlar soni, aniqlik foizi, chempionat bosqichi, oxirgi faollik vaqti.
Yosh, familiya, joylashuv va qurilma ma'lumotlari yuborilmaydi. Ota-ona ilovadan chiqish tugmasi bilan ma'lumotni serverdan o'chira oladi.

## Cheklov
Bu oddiy variant: akkauntsiz ishlaydi, shuning uchun texnik bilimli kishi soxta ball yuborishi mumkin. Bolalar o'yini uchun bu odatda yetarli.

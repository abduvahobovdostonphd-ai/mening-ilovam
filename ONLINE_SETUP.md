# Onlayn reytingni ulash va himoyalash (Firebase)

Ilova ballarni bepul Firebase Realtime Database'da saqlaydi. Himoya 3 qatlamdan iborat:
1. **Anonim kirish**: faqat ilovaning o'zi ma'lumotni o'qiy oladi (tokensiz so'rovlar rad etiladi).
2. **Faqat egasi yozadi**: har bir o'yinchi yozuvi qurilma identifikatori bilan boshlanadi, boshqa qurilma unga yoza ham, o'chira ham olmaydi.
3. **Server tekshiruvi**: ball bir zumda sakrab ketolmaydi (vaqt o'tishi bilan cheklangan tezlikda o'sadi), noma'lum maydonlar va soxta vaqt rad etiladi.

## Sozlash (bir marta)
1. **Anonim kirishni yoqing:** Firebase → **Build → Authentication → Get started → Sign-in method → Anonymous → Enable → Save**.
2. **Web API Key ni oling:** ⚙️ **Project settings → General** sahifasida «Web API Key» yoziladi.
   (Ko'rinmasa: shu sahifada pastda **Add app → Web (</>)** bosing, chiqqan `apiKey` qiymatini oling.)
3. **GitHub'da `www/config.js` ni oching** (qalamcha) va `window.KARRA_API_KEY = "..."` ichiga kalitni qo'ying → **Commit changes**. APK avtomatik qayta yig'iladi.
4. **Eski sinov ma'lumotlarini o'chiring:** Realtime Database → **Data** → `players` yonidagi ✖ → o'chirish.
5. **Qoidalarni almashtiring (eng oxirida):** **Rules** bo'limiga `firebase-rules.json` mazmunini joylang → **Publish**.
   Shundan so'ng ma'lumotlar bazasi ochiq emas: faqat anonim kirgan ilovalar ishlaydi.

Tekshirish: Rules bo'limidagi **Rules Playground** da `/players` ni tokensiz o'qishga urinsangiz, «Denied» chiqishi kerak.

## Nimalar saqlanadi
Faqat ota-ona ruxsat bergan o'yinchilar: ism (familiyasiz), rasm, ballar, o'yinlar soni, aniqlik foizi, chempionat bosqichi, oxirgi faollik vaqti.
Yosh, familiya, joylashuv yuborilmaydi. Ota-ona ilovadagi «Onlayn reytingdan chiqish» tugmasi bilan ma'lumotni serverdan o'chiradi.

## Cheklovlar (halol)
- Ball qurilmada hisoblanadi, shuning uchun texnik bilimli kishi sekin-asta (server ruxsat bergan tezlikda) soxta ball yig'ishi mumkin.
  To'liq himoya uchun hisob-kitob serverda (Cloud Functions, pullik Blaze reja) va App Check bo'lishi kerak.
- Kimdir ko'p anonim akkaunt ochib, ko'p soxta o'yinchi yaratishi mumkin. Buni Firebase konsolida kuzatib, kerak bo'lsa `players` dan qo'lda o'chirish mumkin.

# Sinolife Collagen — landing (LandingPage-3)

Uchinchi variant: sarlavhasi «teri, soch va boʻgʻimlar uchun dengiz kollageni».
Sayt butunlay statik — `public/` papkasi (index.html + img/ + fonts/).

**Pages manzili:** https://forwork7002.github.io/LandingPage-3/

## Deploy

Sayt **`gh-pages` branchidan** beriladi (Settings → Pages → Deploy from a
branch: `gh-pages` / root). `main` ga har push boʻlganda
`.github/workflows/pages.yml` ishga tushadi: `public/` ni `_site` ga
koʻchiradi, `og:image`/`og:url` teglarini saytning haqiqiy manzili bilan
almashtiradi va `gh-pages` branchini yangilaydi.

Nega `actions/deploy-pages` emas: bu repoda `GITHUB_TOKEN` ga Pages sayti
yaratish huquqi yoʻq (`Create Pages site failed: Resource not accessible by
integration`), shuning uchun branch orqali deploy qilinadi — u faqat
`contents: write` talab qiladi.

Custom domain ulasangiz, workflow ichidagi `BASE_URL` ni oʻsha domenga
oʻzgartiring (hozir u repo nomidan avtomatik yigʻiladi).

`server.js`, `start.sh`, `sinolife-landing.service` repoda qoladi, lekin
saytga chiqmaydi — ular faqat oʻz serveringizda ishlatish uchun.

## Sozlash

`public/index.html` ichidagi `CONFIG` bloki:

- `phone`, `phoneLink`, `telegram`, `instagram` — kontaktlar
- `callbackText` — operator qachon qoʻngʻiroq qilishi haqidagi matn
- `leadEndpoint` — buyurtma yuboriladigan manzil (standart `/api/lead`)
- `videos` — YouTube video id lari

## Buyurtma formasi haqida muhim eslatma

GitHub Pages — statik hosting, unda backend yoʻq. Shuning uchun Pages'dagi
nusxada forma `/api/lead` ga yozilganda xato beradi. Formaning ishlashi uchun
ikki yoʻl bor:

1. `server.js` ni oʻz serveringizda ishga tushiring (`start.sh`, Bitrix24
   webhook `BITRIX_WEBHOOK` env orqali) va saytni oʻsha yerdan bering; yoki
2. `leadEndpoint` ga tashqi manzil yozing, masalan
   `https://api.sizning-domen.uz/api/lead` (server tomonda CORS ochilishi kerak).

## Lokalda koʻrish

```sh
./start.sh          # yoki: node server.js
# → http://localhost:3000
```

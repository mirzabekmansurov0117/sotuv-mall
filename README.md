# SOTUV MALL

O‘zbek tilidagi marketplace demo ilovasi. React + Vite frontend va Node.js API, JSON faylli ma’lumotlar ombori bilan ishlaydi. Qoramtir glassmorphism interfeysda xaridorlar ro‘yxatdan o‘tishi, mahsulotlarni taklifli qidiruv orqali topishi, filtrlashi, saqlashi, savat va buyurtmalarni boshqarishi mumkin. Administrator ko‘p rasmli mahsulotlar va buyurtmalarni boshqaradi.

## Ishga tushirish

Node.js 20.19 yoki yangiroq kerak.

```bash
npm install
npm run dev
```

Frontend `http://localhost:5173`, API `http://localhost:3001` manzilida ishlaydi. Ishlab chiqarish yig‘masi uchun `npm run build`, keyin `npm start` buyrug‘idan foydalaning. `PORT` o‘zgaruvchisi server portini belgilaydi. Mahsulotlar va buyurtmalar `data/store.json` faylida saqlanadi; deploy paytida bu papka uchun doimiy disk biriktiring.

## Administrator hisobi

Yangi mahalliy bazada birinchi ishga tushishda admin email va tasodifiy kuchli parol terminalda bir marta ko‘rsatiladi. Ularni xavfsiz joyda saqlang. O‘zingiz belgilash uchun `.env` fayliga `ADMIN_EMAIL` va `ADMIN_PASSWORD` qiymatlarini yozing (`.env` Git’ga qo‘shilmaydi). Production muhitida ikkalasi ham majburiy; parol kamida 16 belgi bo‘lishi kerak. Mijoz parollari foydalanuvchiga xos salt bilan scrypt yordamida xeshlanadi, sessiyalar 7 kundan keyin tugaydi va HttpOnly cookie orqali uzatiladi.

## Deploy

`npm install && npm run build` bajarib, ilovani `npm start` bilan ishga tushiring. Node.js jarayoni `dist` ichidagi front-end fayllarni va API’ni bir portda taqdim etadi. Birinchi production ishga tushirishda `NODE_ENV=production`, `ADMIN_EMAIL` va `ADMIN_PASSWORD` ni sozlang. Tashqi reverse proxy’da HTTPS yoqing va `data/` katalogini zaxiralang. Rasmlar tashqi URL yoki mahsulot formasiga yuklangan rasm fayli sifatida saqlanishi mumkin.

### Render’da bepul preview

`render.yaml` Render’da `sotuv-mall` web service’ni bepul reja bilan yaratadi va admin parolini Render’da tasodifiy yaratadi. Bepul service 15 daqiqa so‘rov kelmasa uxlaydi; `data/` ichidagi akkauntlar, buyurtmalar va yuklangan rasmlar qayta ishga tushganda yo‘qolishi mumkin. Buni production ma’lumotlari uchun ishlatmang. Doimiy ma’lumot saqlash uchun persistent database va pullik service kerak bo‘ladi.

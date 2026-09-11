[🇺🇿 O'zbekcha](README.md) | [🇬🇧 English](README.en.md) | [🇷🇺 Русский](README.ru.md)

# idy@wahhid — shaxsiy blog

Flask asosida qurilgan, terminal/kod estetikasidagi shaxsiy blog va kundalik platformasi. Qorong'i tungi tema, `$` prompt uslubi va to'liq funksional admin panel bilan.

## Xususiyatlar

- 📝 Maqolalar (blog postlar) — yozish, tahrirlash, qoralama sifatida saqlash, avtosaqlash
- 🖼️ Galereya — rasm albomlari va media boshqaruvi
- 💬 Fikr-mulohaza (feedback) va kontakt formasi — IP bo'yicha rate-limit bilan himoyalangan
- 📧 Gmail SMTP orqali yangi xabarlar haqida email bildirishnoma
- 🔐 Admin panel — login (brute-force himoyasi bilan), sozlamalar, xabarlarga javob berish
- 🎨 Terminal uslubidagi qorong'i dizayn (JetBrains Mono, yashil accent)

## Texnologiyalar

- **Backend:** Python, Flask 3
- **Ma'lumotlar bazasi:** SQLite
- **Server:** Gunicorn (production uchun)
- **Rasmlar bilan ishlash:** Pillow
- **PDF generatsiya:** ReportLab

## O'rnatish

```bash
git clone https://github.com/idywahhid/veb-blog.git
cd veb-blog

python3 -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt

cp .env.example .env
# .env faylini to'ldiring (SECRET_KEY, ADMIN_PASSWORD_HASH va h.k.)
```

Admin parol hash yaratish:

```bash
python make_hash.py
```

Natijadagi qiymatni `.env` faylidagi `ADMIN_PASSWORD_HASH` ga qo'ying.

## Ishga tushirish

Development rejimida:

```bash
flask --app app run
```

Production uchun:

```bash
gunicorn app:app -c gunicorn.conf.py
```

## Muhit o'zgaruvchilari

| O'zgaruvchi | Tavsif |
|---|---|
| `SECRET_KEY` | Flask maxfiy kaliti (majburiy, production uchun) |
| `DEBUG` | Development rejimi (`true`/`false`) |
| `SESSION_COOKIE_SECURE` | Cookie faqat HTTPS orqali (production'da `true`) |
| `ADMIN_USERNAME` | Admin panel login |
| `ADMIN_PASSWORD_HASH` | `make_hash.py` orqali yaratilgan parol hash |
| `DB_PATH` | SQLite ma'lumotlar bazasi fayl yo'li |
| `CONTACT_EMAIL` / `CONTACT_TELEGRAM` / `CONTACT_LINKEDIN` / `CONTACT_GITHUB` | Kontakt sahifasidagi havolalar |
| `TELEGRAM_CHANNEL` | Telegram kanal havolasi |

Barcha o'zgaruvchilar `.env.example` faylida namuna bilan ko'rsatilgan.

## Loyiha strukturasi

```
├── app.py              # Asosiy Flask ilova
├── admin.py             # Admin panel route'lari
├── auth.py              # Parol hash/tekshirish
├── config.py             # .env dan sozlamalarni o'qish
├── database.py           # SQLite bilan ishlash
├── notifications.py       # Email bildirishnomalar
├── templates/             # HTML shablonlar
├── static/                # CSS, JS, rasmlar
└── requirements.txt        # Python kutubxonalari
```

## Litsenziya va huquq

Shaxsiy loyiha. O'zingizga mos qilib o'zgartirishingiz mumkin.

# 🩺 Healtisin - AI-Powered Healthcare Consultation & Medical Intelligence Platform

[![Laravel Version](https://img.shields.io/badge/Laravel-11.x-FF2D20?style=flat&logo=laravel&logoColor=white)](#)
[![PHP Version](https://img.shields.io/badge/PHP-8.2%2B-777BB4?style=flat&logo=php&logoColor=white)](#)
[![Payment Gateway](https://img.shields.io/badge/Payment-Midtrans%20Snap%202.6-002B49?style=flat)](#)
[![OAuth](https://img.shields.io/badge/Auth-Google%20Socialite-4285F4?style=flat&logo=google&logoColor=white)](#)
[![Database](https://img.shields.io/badge/Database-SQLite%20(Default)%20%7C%20MySQL-blue.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**Healtisin** adalah platform layanan kesehatan digital (*digital health platform*) terintegrasi yang menghadirkan **asisten konsultasi medis berbasis AI**, sistem telekonsultasi, artikel kesehatan terkurasi, dan pembayaran paket konsultasi otomatis menggunakan **Midtrans Payment Gateway**.

Dibangun dengan arsitektur **Laravel 11.x**, platform ini menggabungkan antarmuka pengguna yang responsif dengan **Admin Dashboard** canggih untuk mengelola *dataset training* model AI kesehatan (*custom knowledge base*), log audit sistem, serta manajemen transaksi pembayaran.

---

## 🌟 Mengapa Menggunakan Healtisin?

- 🤖 **24/7 AI Medical Consultation**: Asisten cerdas yang dilatih dengan basis pengetahuan medis terverifikasi untuk memberikan penanganan awal, triase gejala, dan rekomendasi kesehatan umum.
- 💳 **Otomatisasi Pembayaran Midtrans Snap**: Mendukung berbagai metode pembayaran instan Indonesia: **QRIS**, **GoPay**, **ShopeePay**, **Virtual Account (BCA, BNI, Mandiri, BRI)**, dan **Kartu Kredit/Debit**.
- 🧠 **AI Knowledge Base Training Engine**: Panel admin khusus untuk melatih, menyempurnakan, dan menguji respons AI berdasarkan dataset tanya-jawab medis terbaru.
- 🔐 **Multi-Provider OAuth & Keamanan**: Masuk cepat dan aman menggunakan akun **Google Socialite** atau kredensial email terverifikasi.
- 📊 **Audit Trail & Diagnostic Logs**: Pemantauan kesehatan database dan riwayat interaksi pengguna secara real-time via Database Log & File Log Controller.

---

## 🚀 Fitur Utama

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                           HEALTISIN CORE MODULES                            │
├──────────────────────┬──────────────────────┬───────────────────────────────┤
│ 💬 AI Health Chatbot │ 💳 Midtrans Gateway  │ 🧠 AI Training Engine         │
│ Konsultasi interaktif│ Checkout otomatis,   │ Tambah & latih dataset        │
│ triase gejala 24/7.  │ QRIS, VA, E-Wallet.  │ pengetahuan medis (/admin).   │
├──────────────────────┼──────────────────────┼───────────────────────────────┤
│ 📰 Health News Portal│ 🌐 Multilingual Hub  │ 🛡️ Admin & Log Monitor        │
│ Artikel medis & FAQ  │ Bahasa Indonesia &   │ File logging, audit database, │
│ terkurasi dokter.    │ Bahasa Inggris.      │ & manajemen langganan.        │
└──────────────────────┴──────────────────────┴───────────────────────────────┘
```

1. **AI Medical Chatbot Assistant (`/chat`)**:
   - Konsultasi interaktif real-time dengan asisten AI yang mampu menganalisis deskripsi keluhan pengguna secara kontekstual.
2. **AI Knowledge Base & Training Dashboard (`/admin/ai-training`)**:
   - Manajemen *prompt engineering*, penambahan dataset medis, dan pengujian respons bot sebelum dipublikasikan.
3. **Midtrans Payment Gateway Integration (`/pricing` & `/payment`)**:
   - Pembelian paket konsultasi kesehatan dengan notifikasi webhook otomatis (*instant payment verification*).
4. **Portal Informasi & Berita Kesehatan (`/news` & `/faq`)**:
   - Publikasi artikel kesehatan berbasis kategori medis dan FAQ interaktif.
5. **Autentikasi Terintegrasi**:
   - Single Sign-On (SSO) via Google Socialite, reset kata sandi, dan proteksi sesi pengguna.

---

## 🛠️ Tata Cara Instalasi & Menjalankan

### 1. Prasyarat Sistem
- **PHP** >= 8.2 (dengan ekstensi `openssl`, `pdo_sqlite`/`pdo_mysql`, `mbstring`, `curl`, `gd`)
- **Composer** >= 2.x
- **Node.js** >= 18.x & **NPM**
- **Git**

---

### 2. Langkah Instalasi

```bash
# 1. Clone repositori
git clone https://github.com/MasterPandaa/Healtisin.git
cd Healtisin

# 2. Install dependensi PHP (Composer)
composer install

# 3. Install dependensi frontend (NPM)
npm install

# 4. Buat file konfigurasi lingkungan (.env)
cp .env.example .env

# 5. Generate application encryption key
php artisan key:generate

# 6. Jalankan migrasi dan seeder database
php artisan migrate --seed

# 7. Hubungkan direktori storage publik
php artisan storage:link

# 8. Build aset frontend (Tailwind / Vite)
npm run build
```

---

### 3. Konfigurasi Environment (`.env`)

Sesuaikan kunci API penting pada file `.env`:

```env
APP_NAME="Healtisin"
APP_URL=http://localhost:8000

# Database Configuration (Default: SQLite)
DB_CONNECTION=sqlite

# Midtrans Payment Gateway (Sandbox / Production)
MIDTRANS_SERVER_KEY=SB-Mid-server-xxxxxxxxxxxx
MIDTRANS_CLIENT_KEY=SB-Mid-client-xxxxxxxxxxxx
MIDTRANS_IS_PRODUCTION=false
MIDTRANS_IS_SANITIZED=true
MIDTRANS_IS_3DS=true

# Google OAuth Socialite
GOOGLE_CLIENT_ID=your-google-client-id.apps.googleusercontent.com
GOOGLE_CLIENT_SECRET=your-google-client-secret
GOOGLE_REDIRECT_URI=http://localhost:8000/auth/google/callback
```

---

### 4. Menjalankan Aplikasi

Jalankan server aplikasi lokal:

```bash
# Jalankan server Laravel
php artisan serve

# Pada terminal terpisah (untuk hot-reloading asset):
npm run dev
```

Akses portal melalui peramban: **`http://127.0.0.1:8000`**

---

## 📖 Panduan Penggunaan & Alur Layanan

```text
┌─────────────────────────┐      ┌─────────────────────────┐      ┌─────────────────────────┐
│ 1. User Register/Login  │ ───> │ 2. Pilih Paket          │ ───> │ 3. Bayar via Midtrans   │
│    (Email / Google SSO) │      │    Konsultasi Medis     │      │    (QRIS / VA / E-Money)│
└─────────────────────────┘      └─────────────────────────┘      └─────────────────────────┘
                                                                               │
                                                                               ▼
┌─────────────────────────┐      ┌─────────────────────────┐      ┌─────────────────────────┐
│ 6. Admin Latih AI Baru  │ <─── │ 5. Catatan Riwayat Chat │ <─── │ 4. Mulai Chatbot AI     │
│    di Menu AI Training  │      │    Tersimpan di Akun    │      │    Konsultasi Medis     │
└─────────────────────────┘      └─────────────────────────┘      └─────────────────────────┘
```

1. **Masuk ke Akun**: Daftar akun baru atau klik tombol **Login with Google**.
2. **Pilih Paket Layanan**: Kunjungi menu *Pricing* untuk memilih kuota konsultasi yang dibutuhkan.
3. **Selesaikan Transaksi**: Pilih metode pembayaran pada popup Midtrans Snap (misal: scan QRIS).
4. **Mulai Konsultasi**: Buka halaman *Chat* untuk berinteraksi langsung dengan AI Health Assistant.
5. **Panel Admin**: Akses rute `/admin` untuk memonitor riwayat transaksi dan melatih *dataset* AI.

---

## 📦 Struktur Direktori Proyek

```text
Healtisin/
├── app/
│   ├── Helpers/
│   │   └── TextHelper.php          # String sanitation & text formatting helper
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Admin/              # Controller Panel Administrator
│   │   │   │   ├── AITrainingController.php     # Manajemen dataset AI medis
│   │   │   │   ├── DatabaseLogController.php    # Log aktivitas database
│   │   │   │   ├── FileLogController.php        # Log berkas server
│   │   │   │   ├── PricingConfigController.php  # Konfigurasi tarif paket
│   │   │   │   └── NewsController.php           # CMS artikel kesehatan
│   │   │   ├── Auth/               # Login, Register, Socialite Google
│   │   │   ├── ChatController.php  # Logika percakapan AI & message stream
│   │   │   └── PaymentController.php # Integrasi webhook & checkout Midtrans
│   │   └── Middleware/             # Otentikasi & proteksi akses admin
│   └── Models/                     # Eloquent Models (User, Chat, Payment, dll.)
├── database/
│   ├── migrations/                 # Skema tabel transaksi, user, & chat
│   └── seeders/                    # Data awal pricing, admin, & kategori
├── resources/
│   ├── views/                      # Template Blade UI (Public & Admin)
│   ├── css/                        # Sumber stylesheet
│   └── js/                         # Script frontend
├── routes/
│   ├── web.php                     # Rute portal publik & admin
│   └── auth.php                    # Rute otentikasi
├── composer.json                   # Dependensi PHP & Laravel 11
├── package.json                    # Dependensi frontend & asset build
└── README.md                       # Dokumentasi komprehensif sistem
```

---

## 🔒 Privasi & Keamanan Data Medis

- **Enkripsi Data Pengguna**: Seluruh data sensitif dan kredensial diamankan dengan enkripsi standar industri Laravel.
- **Midtrans Webhook Verification**: Verifikasi tanda tangan digital (*signature key hash*) pada setiap notifikasi pembayaran masuk guna mencegah *spoofing*.
- **CSRF & Rate Limiting**: Perlindungan form token dan pembatasan frekuensi pengiriman pesan (*chat rate limiter*) untuk mencegah penyalahgunaan bot.

---

## 📄 Lisensi & Kontribusi

Proyek ini didistribusikan di bawah lisensi [MIT](LICENSE). Terbuka untuk pengembangan riset dan kolaborasi teknologi kesehatan.

Kontribusi, pelaporan kendala (*bug report*), atau penambahan modul medis dapat diajukan melalui [GitHub Issues](https://github.com/MasterPandaa/Healtisin/issues) atau *Pull Request*.

# Healtisin — AI Healthcare Consultation & Triage Platform

[![Laravel Version](https://img.shields.io/badge/Laravel-11.x-FF2D20?style=flat&logo=laravel&logoColor=white)](#)
[![PHP Version](https://img.shields.io/badge/PHP-8.2%2B-777BB4?style=flat&logo=php&logoColor=white)](#)
[![Payment Gateway](https://img.shields.io/badge/Payment-Midtrans%20Snap%202.6-002B49?style=flat)](#)
[![OAuth](https://img.shields.io/badge/Auth-Google%20Socialite-4285F4?style=flat&logo=google&logoColor=white)](#)
[![Database](https://img.shields.io/badge/Database-SQLite%20(Default)%20%7C%20MySQL-blue.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

An online healthcare assistance and medical triage platform built on **Laravel 11**, integrating conversational AI guidance, curated health information portals, and automated transaction handling via **Midtrans Payment Gateway**.

Healtisin combines a patient-facing consultation interface with an administrative dashboard for managing medical knowledge bases, training datasets, and billing logs.

---

## Overview

Accessing preliminary medical guidance often involves high friction or delays. Healtisin offers an automated triage system where patients can input symptoms and receive preliminary guidance before scheduling in-person clinical consultations:

- **Symptom Triage Assistant**: Context-aware consultation chatbot trained on structured health guidelines to provide preliminary health guidance.
- **Midtrans Payment Integration**: Automated package checkout supporting Indonesian payment rails (QRIS, GoPay, ShopeePay, Virtual Accounts).
- **Knowledge Base Administration**: Admin dashboard for curating symptom prompt contexts, verifying source guidelines, and auditing bot responses.
- **Secure Authentication**: Multi-provider login featuring Google OAuth (Socialite) and session management.
- **Audit Trails**: Real-time logging of consultations and transactional verification webhooks.

---

## Architecture & Modules

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                           HEALTISIN CORE MODULES                            │
├──────────────────────┬──────────────────────┬───────────────────────────────┤
│    Health Chatbot    │   Midtrans Gateway   │      AI Training Engine       │
│ Interactive symptom  │ Automated checkout,  │ Knowledge base management,    │
│ triage & Q&A.        │ QRIS, VA, E-Wallet.  │ prompt validation (/admin).   │
├──────────────────────┼──────────────────────┼───────────────────────────────┤
│  Health News Portal  │  Multilingual Hub    │     Admin & Log Monitor       │
│ Curated medical      │ Indonesian & English │ File logging, database audits,│
│ articles and FAQs.   │ interface support.   │ subscription records.         │
└──────────────────────┴──────────────────────┴───────────────────────────────┘
```

1. **Medical Consultation Assistant (`/chat`)**: Contextual interactive chat analyzing symptoms and directing patients to appropriate specialist domains.
2. **Knowledge Base & Prompt Dashboard (`/admin/ai-training`)**: Management interface for prompt adjustments and verified response validation.
3. **Midtrans Billing Engine (`/pricing` & `/payment`)**: Subscription and per-consultation credit processing with instant webhook reconciliation.
4. **Health News & FAQ (`/news` & `/faq`)**: Information library categorized by medical discipline.
5. **Session & Security Layer**: Protected routes with Google OAuth and CSRF token verification.

---

## Installation & Local Setup

### Prerequisites

- PHP >= 8.2 (extensions: `openssl`, `pdo_sqlite`/`pdo_mysql`, `mbstring`, `curl`, `gd`)
- Composer >= 2.x
- Node.js >= 18.x & NPM

### Setup Instructions

1. **Clone the repository**:
   ```bash
   git clone https://github.com/MasterPandaa/Healtisin.git
   cd Healtisin
   ```

2. **Install dependencies**:
   ```bash
   composer install
   npm install && npm run build
   ```

3. **Configure environment**:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. **Set database & Midtrans keys in `.env`**:
   ```env
   DB_CONNECTION=sqlite
   # Atau jika menggunakan MySQL:
   # DB_CONNECTION=mysql
   # DB_DATABASE=healtisin_db

   MIDTRANS_SERVER_KEY=your_midtrans_server_key
   MIDTRANS_CLIENT_KEY=your_midtrans_client_key
   MIDTRANS_IS_PRODUCTION=false
   ```

5. **Run migrations and seeders**:
   ```bash
   php artisan migrate --seed
   ```

6. **Start local development**:
   ```bash
   php artisan serve
   ```
   Access the platform at `http://localhost:8000`.

---

## License

This project is licensed under the [MIT License](LICENSE).

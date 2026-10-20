<p align="center">
  <img src="assets/banner.svg" alt="Healtisin AI Health Banner" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Recognition-PROXOCORIS_International_Semi--Finalist-E11D48?style=flat-square" alt="Recognition">
  <img src="https://img.shields.io/badge/Backend-Laravel_11-FF2D20?style=flat-square&logo=laravel" alt="Laravel">
  <img src="https://img.shields.io/badge/AI_Triage-Knowledge_Base_Engine-059669?style=flat-square" alt="AI Triage">
  <img src="https://img.shields.io/badge/Payments-Midtrans_Snap-0052CC?style=flat-square" alt="Midtrans">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-10B981?style=flat-square" alt="License"></a>
</p>

## Overview

Healtisin is an AI-powered healthcare consultation and clinical assistance platform developed with **Laravel 11**, recognized as an **International Semi-Finalist at PROXOCORIS 2025**.

The platform tackles primary healthcare accessibility barriers by combining automated AI symptom pre-triage with licensed physician scheduling, real-time consultation chats, and integrated payment checkout via Midtrans.

---

## Core Capabilities

- **AI Medical Triage Chatbot**: Evaluates initial patient symptom severity using curated clinical knowledge bases to recommend suitable specialist fields.
- **Physician Booking Directory**: Search doctors by specialization, clinical availability, ratings, and institutional affiliations.
- **Midtrans Payment Integration**: Handles consultation booking transactions via virtual accounts, e-wallets, and QRIS payments.
- **Electronic Health Consultation Logs**: Secure storage for patient diagnosis histories, medical prescriptions, and appointment records.
- **Administrative Telehealth Console**: Comprehensive metrics dashboard for hospital administrators to track booking volumes and revenue.

---

## Quickstart

### Prerequisites

- PHP 8.2 or higher
- Composer and Node.js
- MySQL 8.0+

### Setup Instructions

1. Clone the repository:
   ```bash
   git clone https://github.com/MasterPandaa/Healtisin.git
   cd Healtisin
   ```

2. Install dependencies:
   ```bash
   composer install
   npm install && npm run build
   ```

3. Configure environment:
   ```bash
   cp .env.example .env
   php artisan key:generate
   ```

4. Run database migrations:
   ```bash
   php artisan migrate --seed
   php artisan serve
   ```
   Open `http://localhost:8000` in your browser.

---

## Repository Structure

```text
Healtisin/
├── app/Http/Controllers/   # Doctor directory, booking, and AI triage controllers
├── app/Services/           # AI inference service and Midtrans payment handler
├── database/migrations/    # Database schema for appointments, doctors, and triage
├── resources/views/        # Responsive patient web client and admin portal
└── README.md               # Platform documentation
```

---

## License

This project is licensed under the [MIT License](LICENSE).

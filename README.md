# Bill Saathi AI 🏥🧾

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.12+](https://img.shields.io/badge/python-3.12+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688.svg)](https://fastapi.tiangolo.com)
[![React 18](https://img.shields.io/badge/React-18.3.1-61DAFB.svg)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.6-blue.svg)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-6.0-646CFF.svg)](https://vitejs.dev)
[![Google Gemini](https://img.shields.io/badge/Gemini_2.0-Multimodal_REST-8E75C2.svg)](https://ai.google.dev)
[![Tests Passing](https://img.shields.io/badge/pytest-35%20passed-brightgreen.svg)](https://docs.pytest.org)
[![Security Audited](https://img.shields.io/badge/Security-Session_Isolated_%7C_SHA--256-green.svg)](#privacy-security--ethical-architecture)

> **Factual, Evidence-Based Medical Bill Verification, Regulatory Compliance & Patient Advocacy System for Indian Healthcare.**

Bill Saathi AI empowers patients, families, and healthcare advocates to audit hospital bills against statutory government price ceilings (NPPA / DPCO), identify duplicate charges, verify line-item arithmetic, and generate structured legal dispute dossiers and grievance letters.

---

## 📑 Table of Contents

- [The Healthcare Problem & Mission](#-the-healthcare-problem--mission)
- [System Architecture](#-system-architecture)
- [Core Capabilities & Features](#-core-capabilities--features)
  - [Multimodal Ingestion (JPG, JPEG, PNG, PDF)](#1-multimodal-bill-ingestion-jpg-jpeg-png-pdf)
  - [Deterministic Financial Audit Engine](#2-deterministic-financial-audit-engine)
  - [Side-by-Side Document Review & Outdated Audit Invalidation](#3-side-by-side-document-review--outdated-audit-invalidation)
  - [Patient Advocacy & Legal Grievance Suite](#4-patient-advocacy--legal-grievance-suite)
  - [Privacy, Security & Ethical Architecture](#5-privacy-security--ethical-architecture)
- [Technology Stack](#-technology-stack)
- [Step-by-Step Installation & Setup](#-step-by-step-installation--setup)
  - [Prerequisites](#prerequisites)
  - [Backend Setup](#backend-setup)
  - [Frontend Setup](#frontend-setup)
  - [Environment Configuration (.env)](#environment-configuration-env)
- [API Reference](#-api-reference)
- [Quality Assurance & Automated Testing](#-quality-assurance--automated-testing)
- [🔮 Future Roadmap & Strategic Enhancements](#-future-roadmap--strategic-enhancements)
  - [Phase 1: Expanded Regulatory & Tariff Schedules](#phase-1-expanded-regulatory--tariff-schedules)
  - [Phase 2: 100% Air-Gapped / Browser-Local OCR](#phase-2-100-air-gapped--browser-local-ocr)
  - [Phase 3: ABDM (Ayushman Bharat Digital Mission) Compliance](#phase-3-abdm-ayushman-bharat-digital-mission-compliance)
  - [Phase 4: Insurance TPA Claim Reconciliation & Negotiation](#phase-4-insurance-tpa-claim-reconciliation--negotiation)
  - [Phase 5: Vernacular Multilingual Localization (10+ Indian Languages)](#phase-5-vernacular-multilingual-localization-10-indian-languages)
  - [Phase 6: Mobile Native Apps (Android & iOS)](#phase-6-mobile-native-apps-android--ios)
  - [Phase 7: Community Price Transparency & Crowdsourced Hospital Index](#phase-7-community-price-transparency--crowdsourced-hospital-index)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🩺 The Healthcare Problem & Mission

In Indian healthcare, over **65% of medical expenses are borne out-of-pocket by patients and families**, often during distressing and high-stakes medical emergencies. Patients and caregivers frequently encounter:

1. **Complex Nomenclature & Opaque Coding**: Generic medicines billed under premium brand names, obscure lab procedure codes, and bundled charges that obscure item-level rates.
2. **Statutory Ceiling Overpricing**: Undisclosed billing above statutory price caps mandated by the **National Pharmaceutical Pricing Authority (NPPA)** and **Drugs (Prices Control) Order (DPCO)** for coronary stents, orthopedic knee implants, and scheduled essential formulations.
3. **Double Billing & Duplicate Charges**: Routine clinical charges (e.g., admission fees, nursing administrative charges, surgical tray kits) billed multiple times across departments.
4. **Mathematical & Arithmetic Inconsistencies**: Summation errors, incorrect tax additions on exempt pharmaceuticals, or quantity multiplication discrepancies that go unnoticed.
5. **Information Asymmetry**: Individual patients have no objective benchmark to evaluate whether rates charged align with state norms or statutory ceilings.

### Bill Saathi AI's Core Philosophy

- **Deterministic Verification, Not AI Speculation**: While AI (Google Gemini Multimodal) is used strictly to extract visible document text into structured fields, **all audits, calculations, and rule comparisons are 100% deterministic using Python's exact `Decimal` arithmetic**. We never let an LLM "hallucinate" whether a bill is correct or calculate balances.
- **Factual, Non-Accusatory Advocacy**: We empower patients with polite, formal, gazette-cited inquiries and grievance drafts. Findings are framed around statutory compliance and transparency rather than hostile accusations.

---

## 🏗️ System Architecture

```
                                  +--------------------------------------------------+
                                  |                 Patient / User                   |
                                  |       (Web Browser / Mobile Viewport)            |
                                  +-------------------------+------------------------+
                                                            |
                                      HTTPS (Multipart Upload / JSON API)
                                                            |
                                                            v
+-------------------------------------------------------------------------------------------------------------------+
| FRONTEND LAYER (React 18 + TypeScript + Vite)                                                                     |
|                                                                                                                   |
|  [ Landing Page ] --------> [ Workspace Context ] --------> [ Document Review ] --------> [ Audit & Findings ]    |
|   • Overview                 • Anonymous Session ID          • Side-by-Side Image/PDF      • Severity Badges      |
|   • Case Wizard              • Client-side MIME Checks       • Item Mutation & Versioning  • Legal Grievance Prep |
|   • Sample Case BS-1024      • Live vs. Demo Mode            • Manual Confirmation Flow    • PDF Evidence Dossier |
+-----------------------------------------------------------+-------------------------------------------------------+
                                                            |
                                        REST API / Auth / Session Token
                                                            |
                                                            v
+-------------------------------------------------------------------------------------------------------------------+
| BACKEND LAYER (FastAPI + Python 3.12 + SQLAlchemy 2)                                                              |
|                                                                                                                   |
|  [ File Validation & Security ]               [ Multimodal AI Extractor ]           [ Deterministic Engine ]      |
|   • Magic bytes signature (%PDF-, \x89PNG,     • Google Gemini 2.0 REST API          • Decimal exact arithmetic   |
|     \xff\xd8\xff)                              • inlineData Base64 Image/PDF         • Grand Total vs. Subtotals  |
|   • 15 MB Size & 25 Page Limits                • Zero hallucination prompt           • Line: Qty * Rate == Total  |
|   • Decompression bomb protection              • Uncertainty & reason tagging        • NPPA / DPCO Price Caps     |
|   • SHA-256 deduplication & sanitization       • Fallback to DemoAIProvider          • Clinical duplicate checks  |
|                                                                                                                   |
|  [ Persistence & Repositories ]               [ Document Streaming ]                [ Evidence Dossier ]          |
|   • PostgreSQL / SQLite Offline                • Session-isolated streaming          • ReportLab PDF Generator    |
|   • Bill / BillItem / Verification schemas     • image/jpeg, image/png, pdf          • CSV Findings Export        |
|   • Automatic version incrementing             • Sanitized filesystem path           • Formal Grievance Letters   |
+-------------------------------------------------------------------------------------------------------------------+
```

---

## 🌟 Core Capabilities & Features

### 1. Multimodal Bill Ingestion (JPG, JPEG, PNG, PDF)
- **Direct Image & PDF Processing**: Accepts mobile camera snapshots (`.jpg`, `.jpeg`), high-res mobile screenshots (`.png`), multi-page digital PDFs, and scanned PDFs up to 15 MB.
- **Native Gemini Multimodal REST API**: Transmits raw base64-encoded file bytes with canonical MIME types (`image/jpeg`, `image/png`, `application/pdf`) directly to Gemini via `inlineData`.
- **Zero Hallucination Rules**: Prompt instructions strictly command the AI to extract **only visible, explicit text and numerical values**. Missing fields default to `null` rather than assumed estimates.
- **Confidence & Uncertainty Tagging**:
  - Automatically assesses field confidence; extractions below 0.75 confidence are marked `is_uncertain=True`.
  - Flags arithmetic mismatches (`quantity * unit_price != line_total`) with specific reasons.
  - Automatically transitions bill status to `review_required` whenever uncertain items are present.
- **Truthful Credential Handling**: If `GEMINI_API_KEY` is not configured on the server and live extraction is requested, the system returns an informative notice and tags the bill for manual review rather than falsely claiming automated AI extraction ran.

### 2. Deterministic Financial Audit Engine
- **Fixed-Point Decimal Arithmetic**: Eliminates floating-point rounding bugs (`0.1 + 0.2 != 0.3`) by using Python's `Decimal` with 2 decimal places across all financial calculations.
- **Itemized Summation Verification**: Compares the sum of line totals against billed subtotal and grand total. Detects hidden unitemized overheads.
- **Statutory NPPA & DPCO Price Ceiling Check**:
  - Matches billed medicines and medical devices against National Pharmaceutical Pricing Authority notifications.
  - Flags prices exceeding statutory caps with statutory gazette order numbers, ceiling rates, and exact overcharge amounts.
  - Rejects expired benchmarks to ensure obsolete regulations are never applied.
- **Clinically-Aware Duplicate Detection**:
  - Evaluates clinical context: distinguishes one-time procedural fees (e.g., Admission Fee, Registration, OT Tray Kit) from legitimately repeatable treatments (e.g., daily saline infusions, paracetamol doses, nursing visits).
  - Flags potential duplicate billing with contextual explanations rather than blanket false-positive accusations.

### 3. Side-by-Side Document Review & Outdated Audit Invalidation
- **Visual Verification**: Renders the uploaded document (interactive PDF or native high-resolution image) side-by-side with structured item cards.
- **In-Place Corrections**: Patients can edit item descriptions, quantities, unit prices, or categories.
- **Audit Version Invalidation**: Mutating any item increments the bill's `version` and automatically flags existing audit results as outdated (`is_audit_outdated = True`), prompting the user to re-run verification before generating legal claims.

### 4. Patient Advocacy & Legal Grievance Suite
- **ReportLab Evidence Dossier**: Generates verifiable, branded PDF audit reports summarizing overcharges, duplicate lines, statutory gazette citations, and recommended actions.
- **Custom Grievance Letter Generator**: Pre-populates formal dispute correspondence directed to:
  - Hospital Medical Superintendent / Billing Grievance Desk
  - State Medical Council
  - District Consumer Disputes Redressal Commission (DCDRC / NCDRC)
  - Insurance Ombudsman
- **Affidavit / Declaration Draft**: Generates notarizable declaration drafts compliant with Indian legal standards for insurance reimbursement appeals.
- **CSV Findings Export**: Export structured audit findings for external legal or actuarial review.

### 5. Privacy, Security & Ethical Architecture
- **Session-Scoped Isolation**: Anonymous users receive a secure `X-Session-ID` header token. Bills and documents uploaded under a session token are strictly isolated from other users.
- **Cryptographic File Validation**: Inspects file headers against known magic numbers (`%PDF-`, `\x89PNG`, `\xff\xd8\xff`). Files claiming an extension that mismatch their binary headers are rejected.
- **Decompression Bomb Protection**: Pillow checks image resolution (capped at 10,000 x 10,000 px) to prevent denial-of-service memory exhaustion.
- **Path Traversal Defense**: Uploaded files are renamed using cryptographic UUIDs; physical paths are strictly sanitized with `os.path.basename` before streaming.

---

## 💻 Technology Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Backend Framework** | **Python 3.12+ / FastAPI** | High-performance asynchronous API framework |
| **Database ORM** | **SQLAlchemy 2.0 / Alembic** | Enterprise ORM with declarative mappings and migrations |
| **Databases** | **SQLite (offline) / PostgreSQL / Supabase** | Zero-dependency local development with cloud PostgreSQL readiness |
| **Multimodal AI** | **Google Gemini 2.0 Flash REST API** | Multimodal document parsing (`inlineData` base64) |
| **PDF Generation** | **ReportLab 4.x** | Programmatic PDF evidence dossier compilation |
| **Document Processing** | **pypdf 5.x / Pillow (PIL)** | Binary magic checks, dimensions validation, digital text extraction |
| **Frontend Framework** | **React 18.3 / TypeScript 5.6** | Typed, component-based user interface |
| **Bundler & Dev Server** | **Vite 6.0** | Sub-second HMR and optimized production bundling |
| **Icons & Styling** | **Lucide React / Vanilla CSS** | Custom design system with zero external CSS framework bloat |
| **Testing** | **pytest, pytest-asyncio, Playwright, Node.js** | 35 automated backend tests + end-to-end browser verification |

---

## 🚀 Step-by-Step Installation & Setup

### Prerequisites
- **Python**: Version 3.12 or higher ([Download Python](https://www.python.org/downloads/))
- **Node.js**: Version 18.x or higher ([Download Node.js](https://nodejs.org/))
- **Git**: Installed and configured ([Download Git](https://git-scm.com/))

---

### Backend Setup

1. Open PowerShell or Terminal and navigate to the backend directory:
   ```powershell
   cd "d:\BillSaathi AI\backend"
   ```

2. Create and activate a Python virtual environment:
   ```powershell
   # Windows PowerShell:
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1

   # Linux / macOS:
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Upgrade pip and install backend dependencies:
   ```powershell
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. Configure environment variables:
   ```powershell
   # Windows:
   copy .env.example .env

   # Linux / macOS:
   cp .env.example .env
   ```

5. Run database migrations to create schemas:
   ```powershell
   alembic upgrade head
   ```

6. Seed demo hospitals, pricing benchmarks (NPPA/DPCO), and test bills:
   ```powershell
   python scripts/seed_demo_data.py
   ```

7. Start the FastAPI development server:
   ```powershell
   python -m uvicorn app.main:app --host 127.0.0.1 --port 8000 --reload
   ```

- **Backend Health Check**: [http://127.0.0.1:8000/api/v1/health](http://127.0.0.1:8000/api/v1/health)
- **Interactive Swagger Documentation**: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- **ReDoc Documentation**: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

---

### Frontend Setup

1. Open a second PowerShell or Terminal window and navigate to the frontend directory:
   ```powershell
   cd "d:\BillSaathi AI\frontend"
   ```

2. Install frontend dependencies:
   ```powershell
   npm install
   ```

3. Start the Vite development server:
   ```powershell
   npm run dev
   ```

4. Open your browser and navigate to:
   ```
   http://127.0.0.1:5173/
   ```

---

### Environment Configuration (.env)

The application includes sensible defaults in `.env.example` enabling 100% offline development:

| Variable | Default Value | Purpose |
| :--- | :--- | :--- |
| `PROJECT_NAME` | `Bill Saathi AI` | Application display name |
| `ENV` | `development` | Environment mode (`development` / `production`) |
| `DEBUG` | `true` | Enables verbose debug logging |
| `DEMO_MODE` | `true` | Allows synthetic testing and offline demo extractor |
| `DATABASE_URL` | `sqlite:///./billsaathi.db` | SQLAlchemy connection string (SQLite or PostgreSQL) |
| `SECRET_KEY` | *(auto-generated)* | 32+ character key for JWT token hashing |
| `GEMINI_API_KEY` | *(optional)* | Google Gemini API key for live multimodal extraction |
| `GEMINI_MODEL` | `gemini-2.0-flash` | Gemini model name used for multimodal vision calls |
| `UPLOAD_DIR` | `./uploads` | Local directory for uploaded bill documents |
| `REPORT_DIR` | `./reports` | Local directory for generated PDF dossiers |
| `MAX_UPLOAD_SIZE_MB`| `15` | Maximum upload size per document in megabytes |
| `MAX_PDF_PAGES` | `25` | Maximum page count for PDF documents |

---

## 📡 API Reference

| Method | Endpoint | Description | Auth / Access |
| :--- | :--- | :--- | :--- |
| `GET` | `/api/v1/health` | System health, database connection, and version check | Public |
| `POST`| `/api/v1/auth/register` | Register a new patient or advocate account | Public |
| `POST`| `/api/v1/auth/login` | Authenticate and obtain JWT access token | Public |
| `GET` | `/api/v1/auth/me` | Fetch authenticated user profile | Bearer Token |
| `POST`| `/api/v1/bills/upload` | Upload JPG, PNG, or PDF bill (validates signature, size, pages) | Session / JWT |
| `GET` | `/api/v1/bills` | List bills scoped to current user or `X-Session-ID` | Session / JWT |
| `GET` | `/api/v1/bills/{bill_id}` | Retrieve bill details, extracted items, and status | Owner / Session |
| `GET` | `/api/v1/bills/{bill_id}/document` | Stream original file securely (`image/jpeg`, `image/png`, `application/pdf`) | Owner / Session |
| `PATCH`| `/api/v1/bills/{bill_id}/items/{item_id}` | Correct line item (increments `version`, marks audit outdated) | Owner / Session |
| `POST`| `/api/v1/bills/{bill_id}/items` | Add manual missing line item | Owner / Session |
| `DELETE`| `/api/v1/bills/{bill_id}/items/{item_id}` | Remove erroneously extracted item | Owner / Session |
| `POST`| `/api/v1/verification/verify/{bill_id}` | Execute deterministic audit (arithmetic, DPCO caps, duplicates) | Owner / Session |
| `GET` | `/api/v1/verification/{bill_id}/summary` | Retrieve structured audit discrepancy summary | Owner / Session |
| `POST`| `/api/v1/reports/generate/{bill_id}` | Generate downloadable PDF evidence dossier via ReportLab | Owner / Session |
| `GET` | `/api/v1/reports/download/{report_id}` | Download generated PDF evidence dossier | Owner / Session |

---

## 🧪 Quality Assurance & Automated Testing

### Backend Unit & Integration Tests (35 Tests)
Run the automated test suite with pytest:
```powershell
cd backend
pytest -v
```

The test suite covers:
- **Multimodal Uploads**: Validated with mocked Gemini responses for JPG, PNG, and PDF inputs (`test_multimodal_upload.py`).
- **Input Validation**: Corrupted images (>128 bytes of garbage), invalid file signatures, and unsupported extensions are rejected with HTTP 400.
- **Credential Failure**: Verifies that when `GEMINI_API_KEY` is omitted, the system marks bills `review_required` with clear configuration notices rather than falsely claiming success.
- **AI Fault Tolerance**: Simulates malformed JSON and HTTP 500 server errors from Gemini, ensuring graceful handling without crashing.
- **Deterministic Math**: Verifies Decimal arithmetic on subtotals, grand totals, and line calculations.
- **Statutory Rule Matching**: Validates NPPA price cap matching, overcharge calculations, and rejection of expired benchmarks.
- **Clinically-Aware Duplicates**: Verifies detection of double-billed one-time charges while permitting routine recurring therapies.
- **Session & Document Security**: Tests `X-Session-ID` isolation, preventing unauthorized cross-user access and path traversal.

### Frontend Production Build & Route Testing
```powershell
cd frontend
# 1. Type check and production build
npm run build

# 2. Automated React component & navigation check
node test_react_app.mjs

# 3. Sidebar restructuring & tab regression check
node test_sidebar_restructure.mjs
```

---

## 🔮 Future Roadmap & Strategic Enhancements

The Bill Saathi AI architecture was built modularly to accommodate substantial expansions. Below is our strategic development roadmap:

```
+---------------------------------------------------------------------------------------------------+
|                                  BILL SAATHI AI ROADMAP                                           |
+-----------------------------+-----------------------------+---------------------------------------+
| Phase 1: Regulatory Depth   | Phase 2: Private Edge OCR   | Phase 3: ABDM & ABHA Integration      |
| • CGHS Tier Schedules       | • Client-side WASM OCR      | • FHIR / M3 Health Record Exchange    |
| • Ayushman Bharat PM-JAY    | • Bounding box heatmaps     | • ABHA ID Linkage & Auth Consent      |
| • Automated NPPA Crawler    | • 100% Offline Air-gap Mode | • State Health Authority Gateway      |
+-----------------------------+-----------------------------+---------------------------------------+
| Phase 4: Insurance & TPA    | Phase 5: Vernacular Indic   | Phase 6: Mobile Native & Scanning     |
| • Pre-auth vs. Final Audit  | • 10+ Indian Languages      | • Edge camera capture & glare detect  |
| • Proportionate Deductions  | • Hindi, Tamil, Telugu, etc.| • Offline on-device image enhancement |
| • Form C Dispute Generator  | • Vernacular Grievance Docs | • WhatsApp Assistant Integration      |
+-----------------------------+-----------------------------+---------------------------------------+
|                             Phase 7: Community Price Transparency Network                         |
|                             • Crowdsourced anonymized procedure cost index                        |
|                             • City-wise hospital pricing transparency ranking                     |
+---------------------------------------------------------------------------------------------------+
```

### Phase 1: Expanded Regulatory & Tariff Schedules
- **Central Government Health Scheme (CGHS) Integration**: Ingest official CGHS package rates categorized by NABH / Non-NABH hospital status and city tiers (Tier 1 Metro, Tier 2, Tier 3).
- **Ayushman Bharat PM-JAY Package Tariffs**: Map billed surgical procedures against standard national Health Benefit Packages (HBP 2.2 / 2026).
- **Automated Gazette Web Crawler**: Implement background cron workers to monitor and ingest new price cap notifications from the [NPPA Official Portal](https://nppa.gov.in) and Ministry of Chemicals and Fertilizers.

### Phase 2: 100% Air-Gapped / Browser-Local OCR
- **On-Device WebAssembly OCR (PaddleOCR / Tesseract WASM)**: Enable patients to extract bill data entirely in-browser without sending raw images over the network—ideal for rural, low-bandwidth, or ultra-strict privacy environments.
- **Bounding Box Coordinate Mapping**: Visually link extracted items directly to their bounding box coordinates on the bill document, allowing users to hover over a line item to highlight its position on the original invoice.

### Phase 3: ABDM (Ayushman Bharat Digital Mission) Compliance
- **FHIR / M3 Data Serialization**: Export bill audit findings and clinical itemizations in standard HL7 FHIR formats compatible with Indian National Health Authority (NHA) protocols.
- **ABHA (Ayushman Bharat Health Account) Linkage**: Enable authenticated patients to link their ABHA address, securely pull verified discharge summaries from hospital Electronic Medical Records (EMR), and cross-check them against billed entries.

### Phase 4: Insurance TPA Claim Reconciliation & Negotiation
- **Cashless Pre-Auth vs. Discharge Reconciliation**: Automatically compare the insurer's initial approved pre-authorization letter against the hospital's final discharge bill to pinpoint arbitrary deductions.
- **Proportionate Deduction Verifier**: Detect unlawful "proportionate room rent deductions" where TPAs inappropriately reduce ICU or surgical fees when patients opt for higher room categories.
- **IRDAI Grievance Automator**: One-click generation of IRDAI complaint dossiers with Insurance Ombudsman jurisdiction mapping.

### Phase 5: Vernacular Multilingual Localization (10+ Indian Languages)
- Enable full UI navigation, voice summaries, and grievance document generation in major Indian languages:
  - **Hindi (हिन्दी)**
  - **Bengali (বাংলা)**
  - **Marathi (मराठी)**
  - **Telugu (తెలుగు)**
  - **Tamil (தமிழ்)**
  - **Gujarati (ગુજરાતી)**
  - **Kannada (ಕನ್ನಡ)**
  - **Malayalam (മലയാളം)**
  - **Punjabi (ਪੰਜਾਬੀ)**
  - **Odia (ଓଡ଼ିଆ)**

### Phase 6: Mobile Native Apps (Android & iOS)
- **Document Camera Assistant**: Edge-based document framing, auto-crop, shadow removal, and real-time blur detection to ensure high-accuracy mobile photo capture.
- **WhatsApp Chatbot Assistant**: Allow users in rural or non-technical areas to send a bill photo via WhatsApp to receive an instant, plain-language audio and text audit summary.

### Phase 7: Community Price Transparency & Crowdsourced Hospital Index
- **Anonymized Procedural Pricing Index**: Aggregating de-identified billing data to publish open pricing medians for common procedures (e.g., Normal Delivery, Caesarean, Angioplasty, Cataract Surgery) across hospital chains and metropolitan areas.
- **Fair Billing Hospital Badging**: Recognizing hospitals that demonstrate transparent billing practices, adherence to statutory caps, and zero unbundled duplicate fees.

---

## 🤝 Contributing

We welcome contributions from healthcare advocates, software engineers, legal experts, and data scientists committed to healthcare transparency in India:

1. **Fork the Repository**:
   ```bash
   git clone https://github.com/sahilgaurav18/BillSaathi-AI.git
   ```
2. **Create a Feature Branch**:
   ```bash
   git checkout -b feature/cghs-tariff-integration
   ```
3. **Commit Your Changes with Semantic Messages**:
   ```bash
   git commit -m "feat: add CGHS Delhi NCR 2026 tariff benchmarks"
   ```
4. **Ensure All Automated Tests Pass**:
   ```bash
   pytest
   npm run build
   ```
5. **Open a Pull Request**: Submit your PR with detailed test steps and statutory reference citations where applicable.

---

## 📄 License

This project is open-source and licensed under the [MIT License](LICENSE).

```
MIT License
Copyright (c) 2026 Sahil Gaurav (Team Lakshaya)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

<div align="center">
  <sub>Built with ❤️ for Indian healthcare transparency and patient advocacy.</sub><br>
  <sub><b>Bill Saathi AI (बिल साथी)</b> — Know What to Question.</sub>
</div>

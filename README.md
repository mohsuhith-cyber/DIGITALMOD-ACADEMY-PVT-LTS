# DIGITALMOD ACADEMY — Complete Full-Stack Web Platform

> **"Learn Skills. Build Your Future."**  
> An enterprise-grade, skills-focused education academy website built for **DIGITALMOD ACADEMY PVT (LTD)** in Sungawila Junction, Polonnaruwa, Sri Lanka.

---

## 1. Project Overview & Institutional Identity

- **Brand Name**: DIGITALMOD ACADEMY
- **Proposed Legal Name**: DIGITALMOD ACADEMY PVT (LTD) *(Registration subject to ongoing regulatory formalization)*
- **Certificate Registration Reference**: `PV 00319777`
- **Founder / Director & Registrar**: S.M. Suhith
- **Campus Center**: Sungawila Junction, Polonnaruwa, Sri Lanka
- **Academy Administrative Hotline**: `078 44 500 88` (`+94 78 445 0088`)
- **Student Inquiry & Assistant Hotline**: `076 078 20 85` (`+94 76 078 2085`)
- **Learning Mode**: 100% Offline, In-Person Classroom & Computer Laboratory
- **Medium of Instruction**: Bilingual (English & தமிழ் / Tamil)
- **Credential Assessment Framework**: UBE Approved Assessment Framework (Sequential IDs `DMA/100000` to `DMA/101000` and UBE IDs with instant QR Code Validation)

---

## 2. Technology Stack

- **Framework**: Next.js 16.4+ (App Router with Partial Prerendering and Turbopack)
- **UI Library & Styling**: React 19, Tailwind CSS v4, Lucide React Icons
- **Database & Backend**: Supabase PostgreSQL with complete Row Level Security (RLS) policies
- **Authentication**: Role-based access control (`student` vs `admin`) with secure session handling
- **QR Code Engine**: `qrcode` library for dynamic, cryptographic certificate validation URLs
- **SEO & Discoverability**: Dynamic `sitemap.xml`, `robots.txt`, OpenGraph metadata, and structured data

---

## 3. Design System & Brand Palette

- **Primary Background**: Deep charcoal / near-black (`#090D16` / `#0C111D` / `#121826`)
- **Accent Color**: Warm yellow / gold (`#F59E0B`, `#FBBF24`, `#D97706`)
- **Secondary Tones**: Pure white, slate neutral borders (`#E2E8F0` in light, `rgba(255,255,255,0.08)` in dark)
- **Theme Toggle**: Default Dark Mode with instantaneous Light Mode switcher, persisted in `localStorage`
- **Bilingual Switch**: English / Tamil switcher on top navigation and mobile drawer with Unicode font support (`Nirmala UI`, `Latha`)
- **Original Assets**: Preserved academy crest with golden laurel wreath, graduation cap & pen nib, red stars, and yellow banner (`/public/images/logo.png`)

---

## 4. Complete Application Route Directory (29 Routes)

### Public Website
1. `/` — Homepage with Hero, 4 Featured Courses, 5 Departments, About Section, Learning Benefits, Faculty Notice, FAQ Accordion, Admission CTA, and Campus Location
2. `/courses` — All Courses catalog with live search, department filter, and fee filter
3. `/courses/[slug]` — Comprehensive 14-point course syllabus, schedule, fees, eligibility, and WhatsApp inquiry
4. `/departments` — 5 Academic Faculties (IT, Languages, Psychology, Business, Vocational) with proposed curricula
5. `/about` — Academy heritage, leadership by Director S.M. Suhith, and Sungawila center story
6. `/vision-mission` — Institutional vision, mission statement, and core values
7. `/why-choose-us` — Practical computer lab, QR verification, bilingual mentorship, and affordability
8. `/apply` — Admission application with telephone validation, 25 Sri Lanka districts, reference number generation, and WhatsApp alert
9. `/verify` — Database-backed certificate verification with instant QR generator, Verified, Revoked, and Not-Found states
10. `/accreditation` — Regulatory disclosures regarding corporate registration, UBE approval, and certificate issuance
11. `/faq` — Categorized searchable directory (General, Admissions, Certificates, Payments)
12. `/contact` — Campus address at Sungawila Junction, dual phone hotlines, and message form
13. `/privacy` — Student privacy policy and data protection controls
14. `/terms` — Academic regulations, 80% attendance rule, and code of conduct
15. `/refund` — Tuition fee cancellation and installment guidelines
16. `/_not-found` — Custom 404 page with quick navigation links
17. `/robots.txt` & `/sitemap.xml` — Search engine index rules

### Student Portal
18. `/student/login` — Student sign-in via application reference or email
19. `/student` — Student dashboard with enrolled courses, batch schedules, payment receipts, and certificate download links

### Administrative Command Center
20. `/admin/login` — Administrative access portal with security passkey
21. `/admin/dashboard` — Overview metrics (total students, review items, payments, certificates)
22. `/admin/admissions` — Full application pipeline (Accept, Reject, Waitlist, Admin Notes)
23. `/admin/courses` — Course fee editing, durations, and publish/unpublish toggle
24. `/admin/payments` — Manual fee accounting (Bank Transfer & Cash at Sungawila), balance calculations, and confirmation
25. `/admin/certificates` — Certificate issuance (`DMA/100000`–`DMA/101000`), revocation with reasons, and QR generation
26. `/admin/settings` — Campus hotline editing and immutable audit log trail

---

## 5. Local Development Setup

### Prerequisites
- Node.js `v20.x` or `v24.x`
- npm `v10.x` or `v11.x`

### Installation Steps
```bash
# Clone or navigate to the repository
cd "f:\Digital Mod Academy\webdite"

# Install dependencies (already executed)
npm.cmd install

# Run the local development server with Turbopack
npm.cmd run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Development Access Credentials
- **Admin Portal**: [http://localhost:3000/admin/login](http://localhost:3000/admin/login)
  - Authorized Passkey: `dma@admin2025` (or `admin123`)
- **Student Portal**: [http://localhost:3000/student/login](http://localhost:3000/student/login)
  - Enter any submitted application reference (e.g. `DMA-APP-2025-1001`) or student email.

---

## 6. Database Configuration (Supabase PostgreSQL)

The schema and security policies are fully written in:
- `supabase/migrations/20250101_initial_schema.sql` (Tables & RLS policies)
- `supabase/seed.sql` (Initial departments, draft courses, and verified certificates)

### Applying to Your Supabase Project:
1. Create a free project at [supabase.com](https://supabase.com).
2. Open the **SQL Editor** in your Supabase dashboard.
3. Paste the contents of `supabase/migrations/20250101_initial_schema.sql` and click **Run**.
4. Paste the contents of `supabase/seed.sql` and click **Run**.
5. Copy your **Project URL** and **Anon Key** from *Project Settings -> API*.
6. Update your `.env.local` file:
   ```env
   NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
   NEXT_PUBLIC_SUPABASE_ANON_KEY=your-actual-anon-key
   SUPABASE_SERVICE_ROLE_KEY=your-service-role-key
   ```

*Note: The platform includes built-in offline/local storage resilience. Even before connecting remote Supabase credentials, all forms, admin actions, payments, and certificate verifications work seamlessly!*

---

## 7. Row Level Security (RLS) Policy Summary

| Table | Public Access | Student Access | Admin Access |
|---|---|---|---|
| `courses` | Read published courses only | Read published courses | Full CRUD |
| `departments` | Read all | Read all | Full CRUD |
| `applications` | Insert new application | Read own application | Full CRUD & Status Update |
| `certificates` | Read Verified & Revoked status only (Safe columns) | Read own certificate | Full Issuance & Revocation |
| `payments` | None | Read own payment records | Full Management & Confirmation |
| `profiles` | None | Read & Update own non-role fields | Full Management |
| `audit_logs` | None | None | Read-only |

---

## 8. Manual Payment Accounting Workflow

1. Students submit course admission on the website.
2. The student deposits course fees via bank transfer or brings cash directly to the Sungawila Center.
3. Administrator logs in to `/admin/payments`, clicks **Record Manual Payment**, enters the student name, phone, course fee, and amount paid.
4. The remaining balance is automatically computed and displayed in LKR.
5. Once payment is confirmed by the Director, the payment is marked **Confirmed**, updating the student portal statement.

---

## 9. Certificate Verification & UBE ID Workflow

1. The Director/Registrar issues a certificate at `/admin/certificates` using sequential numbering (e.g. `100174` or `DMA/100000`).
2. An instant QR code linking to `/verify?id=100174` is generated.
3. When scanned or queried on `/verify`, the database validates the record and returns:
   - Certificate Status: **Verified**
   - Public Student Name: `M.M. Fathima Azza`
   - Course: `Computer Science Certificate Course`
   - Exam Date & Grade: `07/02/2025 • Grade A`
   - Registration Number: `PV 00319777`
   - Signatory: `S.M. SUHITH, Director & Registrar`
4. If a certificate is revoked, the public view clearly displays **Revoked** without exposing confidential administrative internal notes.

---

## 10. Production Deployment (Vercel)

1. Push your repository to GitHub or GitLab:
   ```bash
   git init
   git add .
   git commit -m "Initial complete release of DIGITALMOD ACADEMY platform"
   ```
2. Import the repository in [Vercel](https://vercel.com).
3. Add the environment variables from `.env.example` in the Vercel project settings.
4. Click **Deploy**. Vercel will automatically build the 29 routes using Next.js Turbopack.

---

## 11. Backup & Disaster Recovery

- **PostgreSQL Database**: In Supabase, enable daily automated backups under *Database -> Backups*. You can also take manual SQL dumps via `pg_dump`.
- **Uploaded Assets**: Course cover images and certificate templates in `/public/images/` are committed to version control for safe preservation.

---

*© 2025 DIGITALMOD ACADEMY PVT (LTD). All rights reserved.*

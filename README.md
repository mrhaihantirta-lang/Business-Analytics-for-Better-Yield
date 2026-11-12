# BABY — Business Analytics for Better Yield
**iPhone Business Management & Analytics Platform (Malaysia–Indonesia)**
> *Buy Smart. Calculate Better. Grow Further.*

Platform analisis dan pengelolaan bisnis jual beli iPhone second dari Malaysia ke Indonesia dengan pemisahan ketat antara modal pembelian aktual, nilai referensi kepabeanan, dan harga penadah di Indonesia, serta sistem snapshot historis.

## Fitur Utama

1. **Dashboard Analitik**: 8 KPI bisnis utama, 5 grafik performa Recharts (Profit, Revenue, Investment, Purchased vs Sold, Profit Trend), Best Performing Trip, Best Profit & Highest ROI Model, Unsold Inventory, dan ilustrasi rute Malaysia–Indonesia.
2. **My Trips (Workflow 8 Tahap)**: Pencatatan trip otomatis (`BABY-TRIP-001`, dst.), biaya tiket dinamis, perencanaan kapasitas operasional, input multi-model iPhone dalam MYR/IDR, biaya operasional aktual (hotel default Rp0, tidak otomatis ditambahkan), pencatatan penjualan dengan validasi stok, analisis break-even & ROI, serta sistem snapshot (`v1`, `v2`, dst.).
3. **Customs Calculation Engine**: Memisahkan skema **Barang Pribadi Penumpang** (memerlukan konfirmasi kelayakan fasilitas USD 500) dan **Impor Non-Personal / Komersial** (tanpa pembebasan USD 500), lengkap dengan label `Simulation`, `Estimated`, `Actual Payment`, dan `Requires Validation`.
4. **Business Calculator**: Simulasi modal, customs, ROI, gross margin, dan break-even secara real-time dengan tombol **Save as Trip**.
5. **Master Database & Reverse Calculation**:
   - **iPhone Customs Reference Database** (69 varian awal seri 13–17, dengan baseline aktual `iPhone 13 128 GB = Rp4.834.505`)
   - **Indonesian Buyer Price Database** (17 entri baseline awal)
   - **Business Parameters** & **Change Logs**
   - **Reverse Calculation Engine** (Transaction A & B historis + alur *Compare → Create Proposed Update → Approve Update*)
6. **Reporting & Export**: Trip Summary PDF, Trip Summary CSV, Purchase Details CSV, Sales Report CSV, Profit & Loss CSV, Customs Calculation Summary CSV, dan Full Database JSON Backup.
7. **Keamanan Single-Owner**: Login terproteksi cookie HTTP-only bertanda tangan HMAC-SHA256 + hash `scrypt`, serta dukungan penuh migrasi ke **Supabase Auth + PostgreSQL + Row Level Security (RLS)** (`supabase/migrations/001_initial_schema.sql`).

## Menjalankan Secara Lokal

```bash
pnpm install
pnpm run dev
```

Buka `http://localhost:3000`.
Kredensial awal mode lokal (tersimpan di `.env.local`, dapat diubah kapan saja melalui menu **Settings**):
- Email: `owner@baby-analytics.id`
- Password: `baby2026`

## Pengujian & Build

```bash
pnpm run typecheck
pnpm run test
pnpm run build
```

## Deploy ke Supabase + Vercel

1. Jalankan SQL migrasi di `supabase/migrations/001_initial_schema.sql` dan `supabase/seed.sql` pada SQL Editor Supabase Anda.
2. Atur environment variables pada Vercel / `.env.local`:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`
   - `SUPABASE_SERVICE_ROLE_KEY` (server-side only)
   - `BABY_SESSION_SECRET`

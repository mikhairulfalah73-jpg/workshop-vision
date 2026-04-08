# Workshop Visi Bersama — Panduan Setup

## File yang Anda Terima
- `index.html` — Halaman guru (akses via HP)
- `dashboard.html` — Dashboard fasilitator (live results)
- `supabase_schema.sql` — Schema database

---

## Langkah 1: Setup Supabase (5 menit)

1. Buka **https://supabase.com** → New Project
2. Isi nama project (contoh: `workshop-visi`), pilih region terdekat
3. Setelah project siap, buka **SQL Editor**
4. Copy-paste isi file `supabase_schema.sql` → Run
5. Buka **Settings → API**, catat:
   - `Project URL` (contoh: `https://abcxyz.supabase.co`)
   - `anon public` key (baris panjang dimulai `eyJ...`)

---

## Langkah 2: Isi Konfigurasi di File HTML

Di **kedua file** (`index.html` dan `dashboard.html`), ganti baris berikut:

```javascript
const SUPABASE_URL = 'GANTI_DENGAN_SUPABASE_URL';
const SUPABASE_ANON_KEY = 'GANTI_DENGAN_SUPABASE_ANON_KEY';
```

Menjadi nilai asli dari Supabase Anda, contoh:

```javascript
const SUPABASE_URL = 'https://abcxyz.supabase.co';
const SUPABASE_ANON_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...';
```

---

## Langkah 3: Deploy ke Vercel (3 menit)

### Opsi A: Via GitHub (Direkomendasikan)

1. Buat repo baru di **https://github.com** (contoh: `workshop-visi`)
2. Upload ketiga file HTML ke repo (drag & drop)
3. Buka **https://vercel.com** → New Project → Import repo
4. Deploy — Vercel otomatis deteksi static HTML
5. Anda dapat domain seperti: `workshop-visi.vercel.app`

### Opsi B: Drag & Drop ke Vercel

1. Buka **https://vercel.com/new**
2. Drag folder berisi file HTML → Deploy

---

## Langkah 4: Saat Workshop

### Fasilitator (gunakan laptop):
1. Buka `https://domain-anda.vercel.app/dashboard.html`
2. Isi nama sekolah, nama fasilitator, buat kode sesi (contoh: `VISI2026`)
3. Klik **Buat Sesi**

### Guru (gunakan HP):
1. Buka `https://domain-anda.vercel.app` (atau `index.html`)
2. Masukkan kode sesi dari fasilitator
3. Isi diagnosis dan voting nilai

### Alur Workshop:
```
Fase 1: DIAGNOSIS
  → Guru isi 5 pertanyaan
  → Fasilitator lihat % realtime di dashboard
  → Setelah semua selesai → klik "Buka Sesi Nilai"

Fase 2: NILAI
  → Guru otomatis pindah ke halaman pilih nilai
  → Pilih 3 dari 30 nilai yang tersedia
  → Fasilitator lihat ranking realtime

Fase 3: SELESAI
  → Fasilitator klik "Tutup Workshop"
  → Semua guru lihat halaman terima kasih
```

---

## Struktur URL

| URL | Untuk siapa |
|-----|-------------|
| `domain.vercel.app/` | Guru (mobile-friendly) |
| `domain.vercel.app/index.html` | Guru (sama) |
| `domain.vercel.app/dashboard.html` | Fasilitator (laptop) |

---

## Tips

- **Bagikan QR code** dari URL guru ke grup WA guru sebelum workshop
- Dashboard tersimpan otomatis — refresh halaman tidak menghapus sesi
- Satu kode sesi bisa digunakan untuk workshop berbeda (buat kode baru per sekolah)
- Data tersimpan permanen di Supabase — bisa dilihat kembali setelah workshop

---

## Troubleshooting

| Masalah | Solusi |
|---------|--------|
| Guru tidak bisa join | Cek kode sesi dan koneksi internet |
| Data tidak muncul realtime | Pastikan Realtime diaktifkan di Supabase |
| Error 401/403 | Cek ANON KEY di konfigurasi |
| Deploy gagal di Vercel | Pastikan file `.html` ada di root folder |

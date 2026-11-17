# LENSA PK 2.0 · BPJS Ketenagakerjaan KC Pamekasan

Layanan Evaluasi & Analisa Pemberi Kerja, versi aplikasi mandiri untuk komputer dan HP.

**Kode di folder ini publik, tetapi tidak berisi data apa pun.** Data PK, kontak, dan catatan hanya ada di
spreadsheet LENSA PK milik Anda dan di browser perangkat Anda (tersandi bila PIN dipasang).

- `index.html` — tampilan komputer: dasbor, daftar perusahaan, rincian tagihan, impor laporan, sinkron, PIN.
- `hp.html` — tampilan HP: aplikasi LENSA yang sama dengan versi Apps Script (Hari ini, Perusahaan, Grup, Jadwal),
  tetapi jalan di HP walau tanpa sinyal. Di layar kecil `index.html` otomatis membuka `hp.html`.

## 1. Pasang di GitHub Pages (sekali)
1. github.com → **New repository** → nama `lensa-pk` → **Public** → Create.
2. **Add file → Upload files** → unggah semua file di folder ini → Commit.
3. **Settings → Pages** → Deploy from a branch → `main` / `(root)` → Save.
4. Buka `https://<nama-akun>.github.io/lensa-pk/` di Chrome/Edge (komputer) dan Chrome (HP) → **Pasang / Tambahkan ke layar utama**.

Memperbarui: unggah ulang `index.html` dan `hp.html` (dan `sw.js` bila berubah) → Commit. Data di perangkat tidak hilang.

## 2. Sambungkan ke spreadsheet LENSA PK (sekali)
Butuh `LENSA_PK.gs` versi 1.15 atau lebih baru di spreadsheet.
1. Spreadsheet → menu **LENSA PK › LENSA 2.0 (aplikasi) › Siapkan sinkron & lihat kunci** → salin KUNCI.
2. **Ekstensi › Apps Script › Terapkan › Deployment baru** → jenis **Aplikasi web** →
   Jalankan sebagai: **Saya** · Yang memiliki akses: **Siapa saja** → Terapkan → salin URL `/exec`.
   (Deployment lama untuk aplikasi HP Apps Script biarkan; sejak 1.15 aplikasi itu hanya terbuka untuk Anda.)
3. LENSA 2.0 di komputer → **Data & pengaturan › Sinkron** → tempel URL + KUNCI → **Sambungkan**.
   Seluruh data spreadsheet ditarik ke perangkat.
4. Perangkat lain (HP): di komputer klik **Salin kode sambung**, kirim ke HP Anda sendiri, tempel di
   Data & pengaturan › Kode sambung → Sambungkan.

Setelah tersambung: sinkron otomatis saat aplikasi dibuka, tiap 5 menit, dan beberapa detik setelah setiap
catatan. Tombol **Sinkron sekarang** ada di menu samping (komputer) dan menu ⋮ (HP).
Tanpa sinyal: catatan tetap tersimpan di perangkat dan terkirim saat sinyal kembali (tidak tercatat dua kali).

## 3. Pasang PIN (sangat dianjurkan di HP)
Data & pengaturan › **Pasang PIN**. Isi data di perangkat lalu tersandi AES-256 dengan kunci dari PIN, dan
terkunci lagi setelah 15 menit ditinggal. Lupa PIN → "Hapus data di perangkat ini" di layar PIN, lalu sambungkan
ulang: data di spreadsheet tetap utuh.

## Impor laporan harian
Seret file laporan ke jendela aplikasi, atau Data & pengaturan › Pilih file: ITW/ITB, Monitoring, Data Badan Usaha,
KPI084/085, Kartu Iuran (CSV atau XLSX, boleh sekaligus). Hanya baris kode pembina HA187580 yang disimpan.
Bila sinkron aktif, laporan ikut dikirim dan diimpor juga di spreadsheet (lalu diteruskan ke Monitor SPPG seperti biasa).

## Tanpa sinkron (opsional)
Spreadsheet → **File › Download › Microsoft Excel (.xlsx)** → pilih file itu di Data & pengaturan. Hapus file
unduhan sesudahnya (berisi data PK).

## Catatan
- Perhitungan memakai mesin LENSA (server.gs) yang sama persis dengan spreadsheet; hasil diuji identik.
- Hubungan dengan Monitor SPPG tetap lewat spreadsheet (setiap 5 menit). Menu ⋮ › Sinkron dengan Monitor SPPG
  di HP memicunya langsung (perlu sinyal).
- Cadangan: Data & pengaturan › Unduh cadangan (.json). Kunci sinkron tidak ikut; bila PIN aktif cadangan ikut terkunci PIN.

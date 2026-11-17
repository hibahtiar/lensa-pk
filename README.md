# LENSA PK 2.0 · BPJS Ketenagakerjaan KC Pamekasan

Layanan Evaluasi & Analisa Pemberi Kerja, versi aplikasi mandiri untuk komputer dan HP.
**Tahap 1 (17 Nov 2026):** mesin data + dasbor komputer, baca & hitung di perangkat. Sinkron antar-perangkat, PIN, dan kerja harian di HP menyusul (tahap 2).

**Kode di folder ini publik, tetapi tidak berisi data apa pun.** Data PK, kontak, dan catatan hanya tersimpan di browser perangkat Anda.

## Pasang di GitHub Pages (sekali)
1. github.com → **New repository** → nama `lensa-pk` → **Public** → Create.
2. **Add file → Upload files** → unggah semua file di folder ini (`index.html`, `sw.js`, `manifest.webmanifest`, `ikon-192.png`, `ikon-512.png`, `README.md`) → Commit.
3. **Settings → Pages** → Deploy from a branch → `main` / `(root)` → Save.
4. Buka `https://<nama-akun>.github.io/lensa-pk/` di Chrome/Edge → ikon **Pasang** di bilah alamat.

## Memindahkan data LENSA PK yang sekarang
1. Buka spreadsheet LENSA PK → **File › Download › Microsoft Excel (.xlsx)**.
2. Di LENSA PK 2.0 → **Data & pengaturan** → **Pilih file** → pilih file .xlsx itu.
   Semua tab (PK, kontak, relasi, catatan, jadwal, riwayat) pindah ke perangkat ini.
3. Hapus file .xlsx unduhan itu dari folder Unduhan setelah selesai (berisi data PK).

## Impor laporan harian
Seret file laporan ke jendela aplikasi, atau Data & pengaturan › Pilih file: ITW/ITB, Monitoring, Data Badan Usaha, KPI084/085, Kartu Iuran (CSV atau XLSX, boleh sekaligus).
Aturan sama dengan LENSA 1.14: hanya baris kode pembina HA187580 yang disimpan; laporan pembina lain ditolak.

## Catatan
- Perhitungan memakai mesin LENSA 1.14 yang sama persis (diuji: STATUS_PK, GRUP, PERUSAHAAN, PENGURUS, RELASI, RIWAYAT_BAYAR identik).
- Sampai tahap 2 selesai, LENSA 1.14 di spreadsheet tetap dipakai untuk kerja harian & sinkron dengan Monitor SPPG.
- Cadangan: Data & pengaturan › Unduh cadangan (.json). Simpan di tempat aman.

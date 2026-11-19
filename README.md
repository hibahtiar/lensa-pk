# LENSA PK 2.0 · BPJS Ketenagakerjaan KC Pamekasan

Layanan Evaluasi & Analisa Pemberi Kerja, versi aplikasi mandiri untuk komputer dan HP.
Versi 2.3.0 · butuh `LENSA_PK.gs` 1.21 (18 Nov 2026).

**Kode di folder ini publik, tetapi tidak berisi data apa pun.** Data PK, kontak, dan catatan hanya ada di
spreadsheet LENSA PK milik Anda dan di browser perangkat Anda (tersandi bila PIN dipasang).

- `index.html` — satu aplikasi untuk komputer dan HP: aplikasi LENSA yang sama dengan versi Apps Script
  (Hari ini, Perusahaan, Grup, Jadwal, kontak, catat, templat, pesan massal) ditambah **Dasbor**, **Antrean WA**,
  dan **Data & pengaturan** (sinkron, PIN, impor, cadangan). Jalan walau tanpa sinyal.
  - Komputer: tata letak sama dengan Monitor SPPG — menu kiri (≥ 1100 px; 760–1099 px menu ikon), isi di tengah
    (maks 1320 px), rincian PK di laci kanan 560 px (tutup dengan ×, Esc, atau klik di luar laci).
  - HP: navigasi bawah seperti biasa; Dasbor, Antrean WA, Data, dan Perangkat & pengguna ada di menu ⋮.
- Tampilan Apps Script lama sudah ditutup (sejak `LENSA_PK.gs` 1.21): LENSA PK hanya dipakai lewat aplikasi ini.
- `hp.html` — hanya meneruskan ke `index.html` (untuk pintasan lama).
- `sw.js`, `manifest.webmanifest`, `ikon-32.png`, `ikon-192.png`, `ikon-512.png` — agar bisa dipasang & jalan tanpa sinyal.

## 1. Pasang di GitHub Pages (sekali)
1. github.com → **New repository** → nama `lensa-pk` → **Public** → Create.
2. **Add file → Upload files** → unggah semua file di folder ini → Commit.
3. **Settings → Pages** → Deploy from a branch → `main` / `(root)` → Save.
4. Buka `https://<nama-akun>.github.io/lensa-pk/` di Chrome/Edge (komputer) dan Chrome (HP) → **Pasang / Tambahkan ke layar utama**.

Memperbarui: unggah ulang semua file (minimal `index.html`, `hp.html`, `sw.js`) → Commit. GitHub Pages bisa menahan versi lama ±10 menit. Data di perangkat tidak hilang.

## 2. Masuk: satu perangkat = satu akses (sejak 2.3)
Setiap perangkat masuk dengan **kode undangan sekali pakai** dan mendapat kunci sendiri, sehingga bisa dicabut satu per satu.
Perangkat yang belum terdaftar tidak bisa membuka data sama sekali.

**Perangkat lama (sudah tersambung dengan KUNCI bersama):** tidak perlu apa-apa. Setelah `LENSA_PK.gs` 1.21 terpasang,
perangkat terdaftar otomatis saat sinkron berikutnya. KUNCI lama masih berlaku **14 hari** sejak pembaruan (atau sampai
Anda menekan **Matikan KUNCI lama**), lalu perangkat baru hanya bisa masuk dengan kode undangan.

**Perangkat baru (milik Anda atau orang lain):**
1. Di perangkat pemilik: menu **Perangkat** (komputer) / ⋮ › **Perangkat & pengguna** (HP) › **Buat kode undangan**.
   Pilih aplikasi (LENSA PK / Monitor SPPG / MyTagihan Desa), untuk siapa, hak (boleh mengubah / hanya melihat),
   dan batas akses (opsional). Kode berlaku 24 jam (bisa 3 / 7 hari), sekali pakai.
2. **Kirim lewat WhatsApp** atau **Salin pesan undangan**.
3. Di perangkat baru: buka alamat aplikasi → tempel pesan / kode undangan (`LPK.…`) → **Masuk**.
   Bila perangkat itu masih menyimpan perubahan yang belum terkirim, perubahan itu dikirim lebih dulu.

**Mencabut:** Perangkat & pengguna › **Nonaktifkan**:
- **Setelah terkirim**: perubahan terakhir di perangkat itu diterima dulu saat ia sinkron, lalu aksesnya dicabut.
- **Cabut sekarang**: semua kiriman ditolak (HP hilang / dicuri).
Setelah dicabut, data aplikasi di perangkat itu dihapus begitu ia tersambung. Perangkat yang **7 hari tidak sinkron**
terkunci (data tetap ada) sampai sinkron berhasil.

**Keluar** dari perangkat sendiri: Data & pengaturan › **Keluar dari perangkat ini** (perubahan dikirim dulu, lalu data dihapus).

**Log:** setiap perubahan dari setiap perangkat tercatat di tab **LOG_AKSES** (waktu, pengguna, perangkat, tindakan, hasil).
Daftar perangkat ada di tab **PERANGKAT**, kode undangan di tab **UNDANGAN** (hanya sidik, bukan kodenya).

**Monitor SPPG & MyTagihan Desa** dikelola dari halaman yang sama setelah disambungkan sekali (alamat /exec + kunci admin
dari spreadsheet masing-masing; kunci admin hanya disimpan di server LENSA).

Setelah tersambung: sinkron otomatis saat aplikasi dibuka, tiap 5 menit, dan beberapa detik setelah setiap
catatan. Tombol **Sinkron sekarang** ada di menu samping (komputer) dan menu ⋮ (HP).
Tanpa sinyal: catatan tetap tersimpan di perangkat dan terkirim saat sinyal kembali (tidak tercatat dua kali).

## 3. Pasang PIN (sangat dianjurkan di HP)
Data & pengaturan › **Pasang PIN**. Isi data di perangkat lalu tersandi AES-256 dengan kunci dari PIN, dan
terkunci lagi setelah 15 menit ditinggal. Lupa PIN → "Hapus data di perangkat ini" di layar PIN, lalu sambungkan
ulang: data di spreadsheet tetap utuh.

## Antrean WA (kirim berurutan)
Menu **Antrean WA** → pilih daftar (Telat 2+, Telat 1, Belum bayar, Risiko migrasi, kelompok, atau pilih sendiri;
dari Dasbor juga bisa: klik angka → **Kirim pesan berurutan**) → pilih templat → kirim.
Setelah tiap pesan jawab **Sudah terkirim?**: **Ya, lanjut** mencatat di LOG_INTERAKSI dan langsung membuka WA kontak
berikutnya. Di komputer satu tab WhatsApp dipakai ulang; **Enter** = sudah terkirim & lanjut, **Esc** = belum.
Antrean yang belum selesai tersimpan di bagian **Sedang berjalan** dan bisa dilanjutkan kapan saja.

## Impor laporan harian
Seret file laporan ke jendela aplikasi, atau Data & pengaturan › Pilih file: ITW/ITB, Monitoring, Data Badan Usaha,
KPI084/085, Kartu Iuran (CSV atau XLSX, boleh sekaligus). Hanya baris kode pembina HA187580 yang disimpan.
Bila sinkron aktif, laporan ikut dikirim dan diimpor juga di spreadsheet (lalu diteruskan ke Monitor SPPG seperti biasa).

## Catatan
- Perhitungan memakai mesin LENSA (server.gs) yang sama persis dengan spreadsheet; hasil diuji identik.
- Hubungan dengan Monitor SPPG tetap lewat spreadsheet (setiap 5 menit). Menu ⋮ › Sinkron dengan Monitor SPPG
  di HP memicunya langsung (perlu sinyal).
- Cadangan: Data & pengaturan › Unduh cadangan (.json). Kunci / token perangkat tidak ikut; bila PIN aktif cadangan ikut terkunci PIN.

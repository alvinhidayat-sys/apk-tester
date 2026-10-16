# Command Center – Aplikasi Android

Pembungkus (WebView) untuk `index_Absen-Lembur_Terkunci.html`. Semua fitur HTML dipertahankan;
HTML dimuat dari `app/src/main/assets/index.html`.

## Cara mendapatkan APK

### Opsi A – GitHub Actions (tanpa install apa pun)
1. Buat repository GitHub baru, unggah seluruh isi folder ini (termasuk folder `.github`).
2. Buka tab **Actions** > workflow **Build APK** (jalan otomatis saat push; atau klik *Run workflow*).
3. Tunggu ±3–5 menit, buka run yang selesai, unduh artifact **CommandCenter-APK** > `app-debug.apk`.
4. Kirim APK ke HP, izinkan "install dari sumber tidak dikenal", lalu install.

### Opsi B – Android Studio
1. Buka folder ini di Android Studio (Hedgehog/Iguana atau lebih baru), tunggu Gradle sync.
2. Menu **Build > Build Bundle(s) / APK(s) > Build APK(s)**.
3. APK ada di `app/build/outputs/apk/debug/app-debug.apk`.

## Memperbarui isi aplikasi
Ganti `app/src/main/assets/index.html` dengan HTML terbaru, naikkan `versionCode`/`versionName`
di `app/build.gradle`, lalu build ulang.

## Tampilan v1.1
- Landing page: kartu menu hanya ilustrasi + nama menu, 2 kolom x 3 baris pas satu layar (tanpa skrol; landscape/tablet menyesuaikan).
- Header: teks "Command Center - SCADA".
- Bottom bar: Beranda, Durasi (CTT / Marking / Dispatch), Callback, Cuti, Absensi, Tema.
- Welcome screen "The Legacy of" + logo KITA selama ±1,5 detik saat aplikasi dibuka.
- Latar belakang bergaya panel SCADA (grid halus + cahaya), mengikuti tema terang/gelap.
- Video header (journey.webm) tidak ikut dibundel sehingga disembunyikan.

## Fitur native yang ditambahkan
- Unduhan Excel/PDF/Word (blob) otomatis tersimpan ke folder **Download** dan langsung dibuka.
- `window.print()` (lembar A4 SPKL, dll.) memakai dialog cetak Android (bisa "Simpan sebagai PDF").
- Warna status bar & navigation bar mengikuti tema terang/gelap halaman.
- Tombol Back: kembali antar-menu, tekan dua kali untuk keluar.
- Pemilih file (input file), dialog alert/confirm JS, indikator loading, layar awal tanpa kedip putih.
- Tautan eksternal dibuka di browser/aplikasi terkait.

## Catatan
- Aplikasi memerlukan internet (Google Apps Script, Google Sheet, dan pustaka CDN: xlsx, exceljs, Chart.js, jsPDF, font).
- APK yang dihasilkan bertanda tangan debug: aman untuk dibagikan internal. Untuk Google Play perlu build release + keystore sendiri.
- Nama aplikasi: `app/src/main/res/values/strings.xml`. Ikon: logo ND dari HTML (`res/mipmap-*`).

# Panduan Memasang e-IKP RSUD Merauke sebagai Aplikasi Android

Isi paket ini: halaman pembungkus (PWA) yang menampilkan aplikasi Apps Script Anda layar penuh.
Setelah di-hosting, aplikasi bisa dipasang dari Chrome Android (ikon sendiri, tanpa bilah alamat).

## Langkah 1 - Siapkan URL Web App
1. Di editor Apps Script: **Deploy > New deployment > Web app**.
2. *Execute as*: **Me**. *Who has access*: **Anyone** (wajib "Anyone" agar login tetap jalan di dalam pembungkus).
3. Salin URL yang berakhiran **/exec**.

## Langkah 2 - Tempel URL ke index.html
Buka `index.html` dengan Notepad, cari baris:

    const APP_URL = "GANTI_DENGAN_URL_EXEC_ANDA";

Ganti tulisan di dalam tanda kutip dengan URL /exec Anda, lalu simpan.

## Langkah 3 - Hosting (pilih salah satu, gratis)

### Opsi A - Netlify Drop (paling mudah, tanpa akun GitHub)
1. Buka https://app.netlify.com/drop dan masuk/daftar.
2. Seret **seluruh folder** ini (yang berisi index.html, sw.js, manifest.webmanifest, folder icons) ke halaman tersebut.
3. Netlify memberi alamat seperti `https://nama-acak.netlify.app`. Anda bisa mengubah namanya di *Site settings > Change site name*.

### Opsi B - GitHub Pages
1. Buat repositori publik baru di GitHub (mis. `eikp`).
2. **Add file > Upload files**, unggah semua isi folder ini (termasuk folder icons), lalu **Commit**.
3. **Settings > Pages > Source: Deploy from a branch > main / (root) > Save**.
4. Tunggu 1-2 menit; alamatnya `https://USERNAME.github.io/eikp/`.

## Langkah 4 - Pasang di HP Android
1. Buka alamat hosting di **Chrome**.
2. Tunggu aplikasi tampil, lalu ketuk **Pasang Aplikasi** (tombol di pojok kanan bawah) atau menu **⋮ > Instal aplikasi**.
3. Ketuk **Instal**. Ikon RSUD muncul di layar utama.
4. Bagikan alamat hosting (bukan URL script.google.com) ke pegawai lain, atau buat kode QR-nya.

## Opsional - Jadikan file APK
1. Buka https://www.pwabuilder.com, masukkan alamat hosting Anda, klik **Start**.
2. Pilih **Package for stores > Android**, ikuti petunjuk, lalu unduh paketnya.
3. Pakai file `.apk` untuk dipasang langsung (aktifkan "Instal dari sumber tidak dikenal"), atau unggah `.aab` ke Google Play Console.

## Catatan penting
- Setiap kali kode Apps Script diubah, buat **New version** pada deployment yang sama. URL /exec tetap, jadi pembungkus tidak perlu diubah.
- Jika Anda membuat deployment baru dengan URL baru, ganti `APP_URL` lagi dan unggah ulang `index.html`.
- Peringatan "aplikasi ini dibuat oleh pengguna Google Apps Script" dari Google bisa tetap tampil di dalam aplikasi.
- Aplikasi butuh internet. Service worker hanya menyimpan kerangka pembungkus, bukan data laporan.
- Jika layar putih/gagal memuat: pastikan akses Web App "Anyone", URL berakhiran /exec, dan buka URL itu langsung di Chrome untuk memastikan jalan.

# ReadME — LaundryKost

Landing page (single page) untuk **LaundryKost**, layanan laundry yang menyasar mahasiswa dan anak kos. Seluruh halaman disusun sebagai satu halaman utuh dengan navigasi gulir (_scroll_) ke setiap section.

## 1. Tema

Tema yang dipilih adalah **layanan laundry / UMKM**, sesuai salah satu contoh tema yang diperbolehkan pada penugasan. Judul situs: _"Laundry Praktis untuk Anak Kos"_.

## 2. Teknologi yang Digunakan

| Aspek      | Pilihan                                                                                                       |
| ---------- | ------------------------------------------------------------------------------------------------------------- |
| Bahasa     | **HTML** (struktur semantik) dan **CSS** (styling tambahan)                                                   |
| Framework  | **TailwindCSS** melalui CDN Play (`https://cdn.tailwindcss.com`)                                              |
| JavaScript | **Tidak ada.** Tailwind Play CDN membawa konfigurasi tokennya sendiri, tidak ada logika program pada halaman. |
| Font       | Font bawaan sistem (`system-ui`, `Segoe UI`, `Roboto`) — tidak ada font yang diunduh.                         |
| Ikon       | **SVG inline** (gaya _stroke_/outline) — bukan icon font                                                      |

`index.html` dan `style.css` saling terhubung melalui tag
`<link rel="stylesheet" href="style.css">` pada bagian `<head>`.

Untuk menjalankan, cukup buka `index.html` di browser. Tidak perlu server dan
tidak perlu `npm install`; koneksi internet hanya dibutuhkan oleh Tailwind CDN.

## 3. Penjelasan Halaman — dari Header sampai Footer

### 3.1 Header / Navbar — `<header>`

Berada di paling atas dan menempel saat halaman digulir, dengan latar putih
transparan (_frosted glass_).

- **Kiri:** logo (ikon mesin cuci di dalam kotak biru muda) + judul website
  **LaundryKost**, yang mengarah ke `#top` untuk kembali ke atas halaman.
- **Tengah:** `<nav>` berisi **2 link navigasi** — `Layanan` (`#layanan`) dan
  `Harga` (`#harga`), memakai _anchor link_ sehingga halaman menggulir ke section
  terkait, bukan berpindah halaman.
- **Kanan:** **1 tombol CTA** yang menonjol — **Pesan Laundry**, menuju WhatsApp.

### 3.2 Hero / Halaman Utama — `<section>`

Bagian pertama yang dilihat pengunjung.

- **Judul utama (H1):** "Laundry Praktis untuk **Anak Kos**", dengan kata
  _Anak Kos_ diberi warna aksen agar menonjol.
- **Sub-judul:** "Urusan pakaian jadi lebih mudah. Nikmati layanan laundry yang
  bersih, wangi, dan terjangkau khusus untuk kebutuhan mahasiswa."
- **Gambar pendukung:** foto area laundry (`image/laundry.jpg`) dengan rasio 4:3.
- **Tombol aksi (CTA):** **Lihat Layanan** menuju `#layanan`, dilengkapi ikon
  panah bawah.
- **Penanda kepercayaan:** Timbangan Transparan dan Gratis Antar-Jemput Kos.

### 3.3 Section Layanan — `<section id="layanan">`

Judul "Layanan Kami" disertai deskripsi pembuka, lalu **grid 3 kartu** layanan
(minimum 3 program sesuai ketentuan).

| Kartu           | Harga         | Lama Pengerjaan |
| --------------- | ------------- | --------------- |
| Cuci Kering     | Rp7.000 / kg  | 2 hari kerja    |
| Cuci + Setrika  | Rp9.000 / kg  | 2–3 hari kerja  |
| Laundry Express | Rp15.000 / kg | 6–12 jam        |

Kartu **Cuci + Setrika** diberi pita "Favorit Mahasiswa" di sudut kanan atas dan
bayangan yang lebih tebal.

### 3.4 Section Harga — `<section id="harga">`

Judul "Harga Terjangkau untuk Mahasiswa" dengan deskripsi, lalu **grid 4 kartu
harga** (Cuci Kering, Cuci + Setrika, Laundry Express, Cuci Sepatu) agar seluruh
tarif mudah dibandingkan dalam satu layar. Di bawahnya ada catatan ramah anak kos
tentang timbangan digital dan gratis antar-jemput.

### 3.5 Section Paket — `<section id="paket">`

Judul "Paket Hemat Anak Kos" dengan deskripsi, lalu **grid 3 kartu paket**:
Mingguan (5 kg, Rp35.000), **Bulanan** (20 kg, Rp130.000), dan Hemat (10 kg,
Rp65.000).

Kartu **Paket Bulanan** dibuat menonjol: dinaikkan sedikit pada layar besar dan
diberi pita "Paling Hemat • Pilihan Mahasiswa". Setiap paket berisi daftar
fasilitas lengkap dengan ikon centang. Kartu paket sengaja tidak memakai tombol,
karena aksi memesan diambil lewat tombol CTA di navbar.

### 3.6 Section Keunggulan — `<section id="keunggulan">`

Judul "Mengapa Anak Kos Memilih Kami?" dengan deskripsi, lalu **grid 4 kartu**:
Timbangan Akurat, Deterjen Lembut, Wangi Berhari-hari, dan Dekat Kampus.

### 3.7 Section Proses — `<section id="proses">`

Judul "Pantau Cucianmu Tanpa Cemas" dengan deskripsi, lalu **4 alur** bernomor:
Dijemput → Dicuci Higienis → Disetrika Uap → Siap Diantar. Tahap terakhir memakai
warna aksen hijau-teal sebagai penanda selesai.

### 3.8 Call To Action Penutup — `<section id="cta">`

Banner biru penuh berisi judul "Cucian Numpuk? Serahkan Pada Ahlinya!" dan
paragraf ajakan. Bagian ini murni penutup visual tanpa tombol, karena titik
konversi di halaman ini sudah dipenuhi oleh tombol "Pesan Laundry" di navbar
(menuju WhatsApp) dan tombol "Lihat Layanan" di Hero (menuju `#layanan`).

### 3.9 Footer — `<footer>`

- **Nama judul website** "LaundryKost" + deskripsi singkat "Laundry praktis,
  bersih, dan terjangkau untuk mahasiswa."
- **3 media sosial** (sesuai ketentuan "pilih 3 dari 4"): **Instagram**
  (`@laundrykost.id`), **TikTok** (`@laundrykost`), dan **YouTube**
  (`@laundrykost`). Ketiganya masih berupa akun yang akan disiapkan, sehingga
  ditulis lengkap dengan keterangan **"(segera hadir)"**.
- **Hak cipta:** `© 2026 LaundryKost. All rights reserved.`

## 4. Sumber Gambar

Gambar pada section Hero disimpan lokal di `image/laundry.jpg` (6000×3376 px).
Sesuai ketentuan pengumpulan, sumber gambar wajib dicantumkan, dan URL tersebut
telah ditulis sebagai komentar HTML tepat di atas elemen `<img>` pada
`index.html`:

- **Sumber:** [A row of washing machines](https://unsplash.com/photos/a-row-of-washing-machines-R5NdfEnbcYo) — Unsplash (lisensi Unsplash, bebas royalti).

Gambar juga diberi atribut `alt` yang menjelaskan isi gambarnya, dan seluruh ikon
dekoratif diberi `aria-hidden="true"` agar tidak terbaca screen reader.

## 5. AI yang Digunakan

- **Nama AI:** OpenCode (asisten AI berbasis terminal).
- **Peran:** membantu menulis ulang, merapikan, dan menata ulang kode
  HTML/CSS/Tailwind dari materi awal, menyusun `style.css` dan dokumen ini, serta
  membuat 21 ikon SVG yang dipakai di halaman.
- **Dipahami dan diperiksa tim:** seluruh kode pada `index.html` dan `style.css`
  telah dibaca, dipahami, dan disesuaikan oleh anggota kelompok sebelum
  dikumpulkan. AI hanya membantu — bukan menyalin kode pihak lain.

## 6. Daftar File dalam Pengumpulan

| File                    | Keterangan                                            |
| ----------------------- | ----------------------------------------------------- |
| `index.html`            | Struktur halaman, terhubung ke `style.css`            |
| `style.css`             | Styling tambahan di luar utility class Tailwind       |
| `image/laundry.jpg`     | Gambar pendukung pada section Hero                    |
| `ReadME.md`             | Dokumen ini                                           |
| `PengerjaanKelompok.md` | Pembagian tugas dan laporan pengerjaan setiap anggota |

Nama file pengumpulan: `Kelompok_N_Penugasan Week 1`, diunggah oleh satu orang
perwakilan tim.

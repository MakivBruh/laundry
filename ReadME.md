# ReadME — LaundryKost

Landing page (single page) untuk **LaundryKost**, layanan laundry yang menyasar mahasiswa dan anak kos. Halaman ini dibangun sebagai satu halaman utuh dengan navigasi gulir (*scroll*) ke setiap section.

---

## 1. Tema

Tema yang dipilih adalah **layanan laundry / UMKM** — sesuai salah satu contoh tema yang diperbolehkan pada penugasan (UMKM, katalog produk, ide lainnya). Judul situs: *"Laundry Praktis untuk Anak Kos"*.

---

## 2. Teknologi yang Digunakan

| Aspek | Pilihan |
|---|---|
| Bahasa | **HTML** (struktur semantik) dan **CSS** (styling tambahan) |
| Framework | **TailwindCSS** melalui CDN Play (`https://cdn.tailwindcss.com`) |
| JavaScript | **Tidak ada.** Tailwind Play CDN menyertakan konfigurasi.token lewat satu blok `<script>`, tidak ada logika program pada halaman. |
| Font | Font bawaan sistem (`system-ui`, `Segoe UI`, `Roboto`, dll.). Tidak ada font yang diunduh dari internet. |
| Ikon | **SVG inline** (gaya *stroke*/outline) — bukan icon font |

Keterangan: `index.html` dan `style.css` saling terhubung melalui tag
`<link rel="stylesheet" href="style.css">` pada bagian `<head>`.

### Struktur folder

```
.
├── index.html              -> struktur halaman
├── style.css               -> styling tambahan
├── ReadME.md               -> dokumen ini
├── image/
│   └── laundry.jpg         -> gambar pendukung pada section Hero
└── laundry.txt             -> catatan referensi awal (tidak dipakai halaman)
```

### Cara menjalankan

Cukup buka `index.html` di browser. Tidak perlu server, tidak perlu `npm install`.
Koneksi internet hanya dibutuhkan oleh Tailwind Play CDN.

---

## 3. Token Desain (dari `tailwind.config`)

Semua class kustom ini didefinisikan di dalam `index.html` pada blok
`<script> tailwind.config = { ... } </script>`.

### 3.1 Warna — 3 warna aksen + skala netral

MengikutiMaterial Design 3. Seluruh warna ditulis dengan awalan `bg-`, `text-`, atau `border-`.

| Token | Nilai | Dipakai untuk |
|---|---|---|
| `primary` | `#006194` | Warna utama: tombol, judul aksen, logo |
| `primary-container` | `#007bb9` | Versi lebih pekat, untuk hover tombol |
| `primary-fixed` | `#cce5ff` | Latar biru muda: badge, ikon di dalam kotak |
| `secondary` | `#565e74` | Aksen kedua |
| `secondary-container` | `#dae2fd` | Latar biru sangat muda: badge, catatan |
| `tertiary` | `#00685f` | Aksen ketiga (hijau-teal) |
| `tertiary-fixed` | `#89f5e7` | Latar teal muda: badge paket, ikon |
| `surface` / `background` | `#f7f9fb` | Latar halaman |
| `surface-container-low` | `#f2f4f6` | Latar section selang-seling |
| `surface-container-lowest` | `#ffffff` | Latar kartu |
| `on-surface` | `#191c1e` | Warna teks utama |
| `on-surface-variant` | `#3f4850` | Warna teks sekunder |
| `outline-variant` | `#bfc7d2` | Garis pemisah |

Dipakai juga token `error`, `surface-container-high`, `surface-container-highest`,
`inverse-*`, dan `outline` sebagai kelengkapan palet Material 3.

### 3.2 Spacing

| Token | Nilai | Pemakaian |
|---|---|---|
| `space-xs` | `0.25rem` | Jarak sangat kecil di dalam ikon/badan |
| `space-sm` | `0.5rem` | Jarak antar label kecil |
| `space-md` | `1rem` | Jarak standar antar elemen |
| `space-lg` | `1.5rem` | Jarak antar kartu dan padding kartu |
| `space-xl` | `2.5rem` | Jarak antar section (vertikal) |
| `margin` | `1rem` | Padding horizontal section di layar kecil |
| `margin-md` | `2rem` | — |
| `margin-lg` | `3.5rem` | Padding horizontal section di layar besar |
| `gutter`, `gutter-md`, `gutter-lg` | `1 / 1.5 / 2rem` | Jarak antar item grid |

### 3.3 Tipografi

Skala ini membuat **hierarki ukuran selalu konsisten** di semua section, karena
utility `text-*` yang sama dipakai berulang (misal `text-headline-lg` untuk
judul setiap section, `text-body-lg` untuk deskripsi).

| Token | Ukuran | Bobot | Pemakaian |
|---|---|---|---|
| `display-lg` | 48px / 56px | 800 | Judul utama (H1) pada Hero |
| `headline-lg` | 36px / 44px | 700 | Judul tiap section (H2) |
| `headline-md` | 24px / 32px | 700 | Sub-judul besar, harga utama |
| `headline-sm` | 20px / 28px | 600 | Nama brand, judul kartu harga |
| `title-md` | 18px / 26px | 600 | Judul kartu (H3) |
| `body-lg` | 16px / 26px | 400 | Paragraf deskripsi section |
| `body-md` | 14px / 22px | 400 | Paragraf isi kartu |
| `body-sm` | 12px / 18px | 400 | Keterangan kecil |
| `label-lg` | 14px / 20px | 600 | Teks tombol (CTA) |
| `label-md` | 12px / 16px | 700 | Badge dan nav link |
| `label-sm` | 11px / 14px | 700 | Pita "Favorit Mahasiswa", label satuan harga |

---

## 4. Pembagian duties antara `index.html` dan `style.css`

- **`index.html`** — semua class utility Tailwind (warna, spacing, tipografi, layout, state `hover:` / `active:`). Tidak ada aturan warna atau layout yang ditulis manual di sini.
- **`style.css`** — hal yang utility class tidak cukup untuk menyatakannya, atau lebih nyaman ditulis manual:
  1. **Reset dasar** — `box-sizing`, `margin`/`padding` body, `-webkit-font-smoothing`.
  2. **Perilaku scroll** — `scroll-behavior: smooth` dan terutama `scroll-padding-top: 5rem`. Ini memperbaiki masalah nyata: karena header bersifat `sticky` setinggi 4rem, tanpa offset tersebut **judul section akan tertutup header** setiap kali link navbar diklik.
  3. **Ikon inline** — kelas `.icon` supaya ikon tidak gepeng di dalam flex container.
  4. **`::selection`** — warna teks saat disorot, mengikuti palet halaman.
  5. **`text-wrap: balance / pretty`** — perataan baris untuk judul dan paragraf.
  6. **Aksesibilitas** — `:focus-visible` (fokus keyboard selalu terlihat) dan `@media (prefers-reduced-motion: reduce)`.
  7. **Gaya cetak** — `@media print` agar tombol CTA tidak tercetak sebagai kotak biru pekat.

---

## 5. Penjelasan Halaman — dari Header sampai Footer

### 5.1 Header / Navbar — `<header>`

Berada di atas halaman dan menempel saat digulir (`sticky top-0`), dengan latar putih transparan (effect *frosted glass* lewat `backdrop-blur-md`).

- **Kiri:** logo (ikon mesin cuci di dalam kotak biru muda) + judul website **LaundryKost**. Menghunjuk ke `#top` untuk kembali ke atas halaman.
- **Tengah:** `<nav>` berisi **2 link navigasi** — `Layanan` (`#layanan`) dan `Harga` (`#harga`). Keduanya memakai *anchor link* sehingga halaman menggulir ke section terkait, bukan berpindah halaman.
- **Kanan:** **1 tombol CTA** yang menonjol — **Pesan Laundry** (berwarna `primary`, menuju WhatsApp).

Navbar memakai `justify-between`: brand di kiri, grup navigasi + CTA di kanan. Jarak
antar link navigasi memakai token `space-md`, sedangkan jarak grup navigasi ke
tombol CTA memakai `space-md` di ponsel dan `space-lg` di layar lebar
(`sm:gap-space-lg`) supaya tidak berdesakan.

### 5.2 Hero / Halaman Utama — `<section>`

Bagian pertama yang dilihat pengunjung.

- **Judul utama (H1):** "Laundry Praktis untuk **Anak Kos**" — kata *Anak Kos* diberi warna `primary` agar langsung menonjol.
- **Sub-judul:** "Urusan pakaian jadi lebih mudah. Nikmati layanan laundry yang bersih, wangi, dan terjangkau khusus untuk kebutuhan mahasiswa." (1–2 kalimat, sesuai ketentuan).
- **Gambar pendukung:** foto area laundry pada `image/laundry.jpg`, terbungkus `overflow-hidden` dengan rasio 4:3.
- **Tombol aksi (CTA):** 1 tombol — **Lihat Layanan** (menuju `#layanan`, memenuhi syarat "CTA menuju section lain"), dilengkapi ikon panah bawah `i-arrow-down`.
- **Penanda kepercayaan:** Timbangan Transparan (`i-badge-check`) dan Gratis Antar-Jemput Kos (`i-truck`).

### 5.3 Section Layanan — `<section id="layanan">`

Judul "Layanan Kami" + deskripsi pembuka, lalu **grid 3 kartu** (minimum 3 program sesuai ketentuan).

| Kartu | Harga | Lama |
|---|---|---|
| Cuci Kering | Rp7.000 / kg | 2 hari kerja |
| Cuci + Setrika | Rp9.000 / kg | 2–3 hari kerja |
| Laundry Express | Rp15.000 / kg | 6–12 jam |

Kartu **Cuci + Setrika** diberi pita "Favorit Mahasiswa" di sudut kanan atas dan shadow lebih tebal.

### 5.4 Section Harga — `<section id="harga">`

Judul "Harga Terjangkau untuk Mahasiswa" + deskripsi, lalu **grid 4 kartu harga** (Cuci Kering, Cuci + Setrika, Laundry Express, Cuci Sepatu) agar seluruh tarif mudah dibandingkan satu layar. Di bawahnya ada **catatan ramah anak kos** tentang timbangan digital (`i-info`) dan gratis antar-jemput (`i-wallet`).

Angka harga memakai `text-headline-md` (24px) — bukan `text-headline-lg` (36px) —
supaya nominal panjang seperti "Rp15.000" tidak memakan lebar kartu. Label satuan
di bawahnya ("per kilogram (kg)", "per pasang sepatu") memakai `text-label-sm`
(11px, uppercase) agar nominal tetap jadi elemen yang paling menonjol.

### 5.5 Section Paket — `<section id="paket">`

Judul "Paket Hemat Anak Kos" + deskripsi, lalu **grid 3 kartu paket**: Mingguan (5 kg, Rp35.000), **Bulanan** (20 kg, Rp130.000), dan Hemat (10 kg, Rp65.000).

Kartu **Paket Bulanan** dibuat menonjol: dinaikkan sedikit di layar besar (`lg:-translate-y-3`) dan diberi pita "Paling Hemat • Pilihan Mahasiswa" (`i-star`). Masing-masing paket berisi daftar fasilitas lengkap dengan ikon centang `i-check-circle`.

Kartu sengaja **tanpa tombol** — isinya murni informasi, dan aksi memesan diambil lewat tombol CTA di navbar. Karena itu `justify-between` (yang awalnya untuk menekan tombol ke dasar kartu) dan margin bawah `mb-space-lg` pada daftar fitur juga dihapus, supaya tidak ada ruang kosong yang sia-sia.

Nominal harga juga memakai `text-headline-md` (24px). Sufiks satuan (`/ paket`, `/ bulan`) memakai `text-body-md` (14px) agar tetap terbaca dan tidak terlihat terlalu kecil dibanding nominal.

### 5.6 Section Keunggulan — `<section id="keunggulan">`

Judul "Mengapa Anak Kos Memilih Kami?" + deskripsi, lalu **grid 4 kartu** (bento): Timbangan Akurat, Deterjen Lembut, Wangi Berhari-hari, dan Dekat Kampus.

### 5.7 Section Proses — `<section id="proses">`

Judul "Pantau Cucianmu Tanpa Cemas" + deskripsi, lalu **4 node alur** bernomor: Dijemput → Dicuci Higienis → Disetrika Uap → Siap Diantar. Node terakhir memakai warna `tertiary` untuk menandai tahap selesai.

### 5.8 Call To Action Penutup — `<section id="cta">`

Banner biru penuh dengan `rounded-3xl` berisi judul "Cucian Numpuk? Serahkan Pada Ahlinya!" dan paragraf ajakan. Bagian ini murni penutup visual (judul + deskripsi) tanpa tombol. Semua titik konversi di halaman ini hanya dua, dan keduanya sudah terpenuhi oleh ketentuan penugasan: tombol "Pesan Laundry" di navbar (menuju WhatsApp) dan tombol "Lihat Layanan" di Hero (menuju anchor #layanan).

### 5.9 Footer — `<footer>`

- **Nama judul website** "LaundryKost" + deskripsi singkat "Laundry praktis, bersih, dan terjangkau untuk mahasiswa."
- **3 media sosial** (sesuai ketentuan "pilih 3 dari 4"): **Instagram** (`@laundrykost.id`), **TikTok** (`@laundrykost`), dan **YouTube** (`@laundrykost`).
- **Hak cipta:** `© 2026 LaundryKost. All rights reserved.`

---

## 6. Daftar Ikon

Ikon pada halaman ini bukan icon font, melainkan **SVG stroke 24×24** yang disimpan
satu kali sebagai 21 `<symbol>` di dalam `<svg class="hidden">` di awal `<body>`,
lalu dipakai 35 kali. Seluruh pemakaian cukup satu baris:

```html
<svg class="icon h-[18px] w-[18px] text-primary" aria-hidden="true">
  <use href="#i-bolt"></use>
</svg>
```

Ikon mewarisi warna teks dari elemen induknya lewat `currentColor`, dan ukurannya
dikendalikan class `w-*` / `h-*` milik Tailwind.

| `id` symbol | Dipakai untuk |
|---|---|
| `i-washer` | Logo di navbar & footer, judul section Layanan, kartu harga Cuci Kering (4×) |
| `i-check-circle` | Daftar fasilitas pada 3 kartu paket (9×) |
| `i-clock` | Jangka waktu pengerjaan 2 hari / 2–3 hari (2×) |
| `i-truck` | Gratis Antar-Jemput Kos di Hero |
| `i-bolt` | Laundry Express di Layanan & Harga (2×) |
| `i-iron` | Cuci + Setrika di Layanan & Harga (2×) |
| `i-sparkles` | Eyebrow "Solusi Pakaian Bersih Bebas Repot" di Hero |
| `i-badge-check` | Timbangan Transparan di Hero |
| `i-arrow-down` | Tombol "Lihat Layanan" di Hero |
| `i-droplet` | Kartu layanan Cuci Kering |
| `i-timer` | Durasi 6–12 jam pada Laundry Express |
| `i-tag` | Eyebrow "Daftar Biaya Bersahabat" di section Harga |
| `i-shower` | Kartu harga Cuci Sepatu |
| `i-info` | Judul "Catatan Ramah Anak Kos" di section Harga |
| `i-wallet` | Eyebrow "Hemat Pengeluaran" di section Paket |
| `i-star` | Pita "Paling Hemat • Pilihan Mahasiswa" |
| `i-gift` | Bonus cuci 1 pasang sepatu di paket Mingguan |
| `i-scale` | Keunggulan Timbangan Akurat |
| `i-spray` | Keunggulan Deterjen Lembut |
| `i-thermo` | Keunggulan Wangi Berhari-hari |
| `i-navigation` | Keunggulan Dekat Kampus |

Tiga symbol (`i-chat`, `i-flower`, `i-user`) sudah dihapus karena tidak lagi dipakai.

---

## 7. Sumber Gambar

Gambar pada section Hero disimpan lokal di `image/laundry.jpg`.

> **TODO - lengkapi:** Sesuai ketentuan pengumpulan, sumber gambar wajib
> dicantumkan. URL sumbernya sudah disiapkan sebagai komentar HTML tepat di atas
> elemen `<img>` pada `index.html` — cukup ganti teksnya dengan URL lengkap
> (contoh: `https://unsplash.com/photos/xxxx` atau
> `https://www.pexels.com/photo/xxxx/`).

Gambar juga diberi atribut `alt` yang menjelaskan isi gambarnya, dan seluruh
ikon dekoratif diberi `aria-hidden="true"` agar tidak terbaca screen reader.

---

## 8. AI yang Digunakan

- **Nama AI:** OpenCode (asisten AI berbasis terminal)
- **Peran:** membantu menulis ulang, merapikan, dan menata ulang kode HTML/CSS/Tailwind
  dari materi awal, menyusun `style.css` dan dokumen `ReadME.md` ini, serta
  membuat 21 ikon SVG di atas.
- **Dipahami dan diperiksa tim:** seluruh kode di `index.html` dan `style.css`
  telah dibaca, dipahami, dan disesuaikan oleh anggota kelompok sebelum
  dikumpulkan. AI hanya membantu — bukan menyalin kode pihak lain.

---

## 9. Checklist Sebelum Mengumpulkan

- [ ] `index.html` — struktur halaman, terhubung ke `style.css`
- [ ] `style.css` — styling tambahan
- [ ] `image/laundry.jpg` — gambar pendukung
- [ ] `ReadME.md` — dokumen ini (**sudah**)
- [ ] Ganti URL sumber gambar pada komentar di `index.html`
- [ ] Ganti URL YouTube `youtube.com/@laundrykost` dengan channel resmi LaundryKost
- [ ] Konfirmasi nomor WhatsApp `6285643429736` sudah milik resmi LaundryKost
- [ ] Bungkus dalam folder/zip bernama `Kelompok_N_Penugasan Week 1`
- [ ] Unggah melalui **1 orang perwakilan tim** saja

> Catatan: `PengerjaanKelompok.md` tidak dibuat — laporan pembagian tugas antar
> anggota kelompok dilaporkan langsung lewat kolom komentar pengumpulan, dan
> pembagian duties `index.html` vs `style.css` sudah dijelaskan di bagian 4 dokumen ini.

---

## 10. Catatan Teknis

- **Tag semantik** yang dipakai: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, `<div>`, `<ul>/<li>`, `<img>`, dan `<a>`.
- **Hierarki heading:** satu `<h1>` (judul Hero), lalu `<h2>` untuk judul setiap section, lalu `<h3>` untuk judul tiap kartu.
- **Tanpa inline style.** Tidak ada atribut `style="..."` di `index.html`; semua pengaturan warna, spacing, dan layout memakai utility class Tailwind, sedangkan perilaku dasar ada di `style.css`.
- **Responsif.** Seluruh grid memakai breakpoint Tailwind (`sm:`, `md:`, `lg:`), sehingga tata letak berubah dari satu kolom di ponsel menjadi dua/empat kolom di layar lebar. Pada layar kecil link navigasi disembunyikan (`hidden sm:flex`) agar tidak berdesakan, sementara tombol CTA "Pesan Laundry" tetap terlihat.
- **Padding halaman di luar `max-w-7xl`.** Semua section memakai pola `px-margin lg:px-margin-lg` pada elemen luarnya, lalu `mx-auto max-w-7xl` di bagian dalam. Navbar mengikuti pola yang sama, dan karena itu jaraknya sama persis dengan section di bawahnya. Kalau padding dan `max-w-7xl` ditukar urutannya, lebar navbar dan section akan berbeda dan konten tampak tidak sejajar.
- **Kode berindeks 2 spasi** dan setiap bagian diberi komentar pembatas agar mudah dibaca dan dipahami.

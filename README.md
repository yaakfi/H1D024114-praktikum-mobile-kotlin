# Praktikum Mobile Kotlin 1 - Aplikasi Jualan

Aplikasi Android berbasis **Jetpack Compose** untuk platform **Jualan**, sebuah wadah yang memfasilitasi produk lokal UMKM di wilayah Kabupaten Purbalingga, Jawa Tengah. Proyek ini mencakup implementasi tata letak deklaratif Compose, sistem navigasi antar-layar (NavHost), komponen Material 3, formulir interaktif, dan kustomisasi tema.

---

## 📱 Tangkapan Layar (Screenshots)

| Layar Tentang Jualan (Basic Info) | Layar Hubungi Kami (Form Kontak) |
| :---: | :---: |
| <img src="docs/screenshots/basic_info_screen.png" alt="Tentang Jualan" width="280"/> | <img src="docs/screenshots/hubungi_kami_screen.png" alt="Hubungi Kami" width="280"/> |

---

## ✨ Fitur Aplikasi

1. **Layar Daftar Produk UMKM (DaftarProdukScreen)**
   - Pengambilan data produk dan kategori secara live dari REST API via **Retrofit**.
   - Integrasi arsitektur **MVVM** menggunakan `ProductViewModel` dan pengamatan reaktif UI State (`StateFlow` / `collectAsState`).
   - Manajemen status UI komprehensif: *Loading* (`CircularProgressIndicator`), *Error* (tampilan pesan galat), dan *Success*.
   - Pemuatan gambar asinkronus dari server internet menggunakan **Coil** (`AsyncImage`).
   - Kolom pencarian (*Search Bar*) interaktif dengan `OutlinedTextField`.
   - Filter daftar produk berdasarkan kategori menggunakan `LazyRow`.
   - Grid produk dinamis menggunakan `LazyVerticalGrid`.
   - Menu aksi di TopAppBar (ikon Cart dan menu dropdown *Hubungi Kami*).
   - Navigasi ke Layar Detail Produk dan Layar Hubungi Kami.

2. **Layar Detail Produk (DetailProductScreen)**
   - Konsumsi data produk live dari `ProductViewModel` berdasarkan `productId`.
   - Pemuatan gambar produk dari server menggunakan `AsyncImage` Coil.
   - Penanganan status UI (*Loading*, *Error*, dan *Success* / produk tidak ditemukan).
   - TopAppBar dengan navigasi kembali (*Back Navigation*).
   - Tampilan detail produk (gambar, nama, harga, deskripsi, dan stok).
   - Pengaturan jumlah beli (*quantity*) dengan tombol minus/plus dan validasi stok produk.
   - Tombol *Tambah ke Keranjang* interaktif dengan umpan balik Toast.

3. **Layar Formulir Kontak (Hubungi Kami Screen)**
   - Penerapan **State Hoisting** dan **Unidirectional Data Flow (UDF)** memisahkan stateful dan stateless composable.
   - Validasi input real-time (format email mengandung '@', panjang pesan minimal 10 karakter).
   - Pilihan tipe pesan dengan `ExposedDropdownMenuBox` (*Pertanyaan*, *Keluhan*, *Saran*).
   - Pemilihan file gambar dari galeri perangkat menggunakan `ActivityResultContracts.PickVisualMedia` (`PhotoPicker`).
   - Kartu pratinjau nama berkas gambar terpilih (`imageUri.lastPathSegment`).
   - Kotak centang persetujuan (*Checkbox*) syarat & ketentuan.
   - Tombol submit yang aktif otomatis hanya saat seluruh kondisi validasi formulir terpenuhi.
   - Notifikasi interaktif *Snackbar* (*"Pesan Terkirim!"*) dengan Coroutine scope.

4. **Layar Informasi (Basic Info Screen)**
   - TopAppBar dengan judul dan ikon informasi.
   - Tampilan logo aplikasi berbentuk melingkar (*circular clip*).
   - Kartu informasi deskripsi platform UMKM lokal Purbalingga.
   - Kartu misi: *Memajukan UMKM Lokal*.

5. **Tema dan Tipografi (Theme & Typography)**
   - Skema warna kustom (Primary, Secondary, Tertiary/PrimaryVariant, Background, Surface).
   - Tipografi Material 3 yang disesuaikan (*headlineMedium*, *titleLarge*, *bodyLarge*, *bodyMedium*, *labelLarge*).

---

## 🛠️ Teknologi & Dependensi

- **Bahasa**: [Kotlin](https://kotlinlang.org/)
- **UI Toolkit**: [Jetpack Compose](https://developer.android.com/jetpack/compose) (Material 3)
- **Arsitektur**: MVVM (Model-View-ViewModel) dengan Kotlin Coroutines & `StateFlow`
- **Networking**: [Retrofit 3.0.0](https://square.github.io/retrofit/) & Gson Converter
- **Image Loading**: [Coil](https://coil-kt.github.io/coil/) (`io.coil-kt:coil-compose:2.6.0`)
- **Navigasi**: [Jetpack Navigation Compose](https://developer.android.com/jetpack/compose/navigation)
- **Min SDK**: API 29
- **Target SDK**: API 37

---

## 🚀 Cara Menjalankan

1. Clone repositori ini:
   ```bash
   git clone https://github.com/yaakfi/H1D024114-praktikum-mobile-kotlin.git
   ```
2. Buka folder proyek di **Android Studio**.
3. Sinkronkan Gradle (*Sync Project with Gradle Files*).
4. Pilih emulator Android atau perangkat fisik yang terhubung (USB debugging aktif).
5. Klik **Run** (`Shift + F10`) atau jalankan perintah Gradle:
   ```bash
   ./gradlew installDebug
   ```

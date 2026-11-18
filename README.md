# 🛒 Katalog Produk UPI Store (JavaFX + SQLite)

Aplikasi desktop GUI modern untuk manajemen katalog produk toko, dibangun menggunakan **Java**, **JavaFX**, **FXML (Scene Builder)**, **CSS**, dan database lokal **SQLite** melalui **JDBC**. Proyek ini menerapkan pola arsitektur **MVC (Model-View-Controller)** dan **Repository Pattern** dengan dukungan operasi **CRUD Lengkap** (*Create, Read, Update, Delete*).

---

## 🌟 Fitur Utama

- **✨ Tampilan Katalog Modern**: Antarmuka responsif berbasis kartu (*card view*) yang tersusun rapi menggunakan `TilePane` dan `ScrollPane`.
- **➕ Tambah Produk (Create)**: Form input untuk menambah nama produk, harga (Rp), serta memilih foto produk contoh.
- **👁️ Baca & Tampilkan Katalog (Read)**: Membaca seluruh data dari database SQLite secara otomatis saat aplikasi dibuka dan menampilkan total jumlah produk.
- **✏️ Edit / Perbarui Produk (Update)**: Mengedit data produk langsung dari kartu katalog. Tombol *Simpan* akan beralih menjadi *Perbarui* dengan opsi *Batal Edit*.
- **🗑️ Hapus Produk (Delete)**: Menghapus produk dari database SQLite dengan dialog konfirmasi keamanan (*Confirmation Dialog*).
- **💾 Persistensi Database Otomatis**: Menggunakan SQLite lokal (`data/katalog.db`). Tabel dan folder otomatis dibuat saat pertama kali aplikasi dijalankan.
- **🎨 Custom Styling (CSS)**: Tampilan visual modern dengan kustomisasi CSS (`app.css`) untuk tombol, form input, efek hover, dan kartu produk dengan sudut membulat (*rounded corners*).

---

## 📂 Struktur Proyek

```text
KatalogProduk/
├── pom.xml                               # Konfigurasi Maven & Dependensi
├── nbactions.xml                         # Pemetaan action Run NetBeans ke javafx:run
├── README.md                             # Dokumentasi proyek & panduan
├── data/                                 # Folder database lokal
│   └── katalog.db                        # File database SQLite (dibuat otomatis saat runtime)
├── src/
│   └── main/
│       ├── java/
│       │   ├── controller/
│       │   │   └── KatalogController.java # Menghubungkan FXML, aksi tombol, dan logic UI
│       │   ├── data/
│       │   │   └── ProdukRepository.java  # Operasi database CRUD (PreparedStatement)
│       │   ├── db/
│       │   │   └── Database.java          # Pengaturan koneksi JDBC SQLite & DDL tabel
│       │   ├── main/
│       │   │   ├── MainApp.java           # Entry point aplikasi JavaFX
│       │   │   └── AppLauncher.java       # Launcher perantara untuk NetBeans / exec
│       │   └── model/
│       │       └── Produk.java            # Entitas model data produk & validasi
│       └── resources/
│           ├── image/                     # Aset gambar produk (roti.png, susu.png, kopi.png)
│           ├── gambar/                    # Salinan aset gambar untuk kompatibilitas
│           └── view/
│               ├── katalog.fxml           # Desain antarmuka (BorderPane)
│               └── styles/
│                   └── app.css            # Styling visual antarmuka JavaFX
```

---

## 🛠️ Prasyarat Sistem

1. **Java Development Kit (JDK)**: Versi 17 atau 21 ke atas.
2. **Apache NetBeans IDE** (disarankan) atau IDE Java lainnya (IntelliJ IDEA / Eclipse / VS Code).
3. **Apache Maven**: Sudah terintegrasi otomatis di dalam NetBeans.

---

## 🚀 Panduan Menjalankan Aplikasi (*How to Run*)

### Opsi 1: Menggunakan Apache NetBeans (Disarankan)

1. Buka **Apache NetBeans**.
2. Pilih menu **File** > **Open Project...** lalu arahkan ke folder **`KatalogProduk`**.
3. Di panel **Projects** (sebelah kiri), klik kanan pada nama proyek **`KatalogProduk`** > pilih **Clean and Build** (atau tekan `Shift + F11`).
4. Setelah muncul tulisan `BUILD SUCCESS`, klik kanan kembali pada **`KatalogProduk`** > pilih **Run** (atau tekan tombol `F6`).
5. Jendela aplikasi *Katalog Produk* akan langsung muncul di layar Anda.

> **Tips NetBeans Goals:**  
> Anda juga dapat menjalankan via menu: Klik kanan project > **Run Maven** > **Goals...** > ketik `clean javafx:run` > klik **OK**.

---

### Opsi 2: Menggunakan Terminal / Command Line (Maven CLI)

Buka terminal (Command Prompt / PowerShell / Bash) di dalam direktori `KatalogProduk`, lalu jalankan perintah:

```bash
mvn clean javafx:run
```

---

## 📖 Panduan Penggunaan Aplikasi

### 1. Menambahkan Produk Baru
1. Masukkan **Nama produk** (contoh: `Roti Cokelat Spesial`).
2. Masukkan **Harga (Rp)** berupa angka bulat tanpa titik (contoh: `12000`).
3. Pilih foto pada dropdown **Foto contoh** (`roti.png`, `susu.png`, atau `kopi.png`).
4. Klik tombol **Simpan**. Produk akan muncul di katalog dan data tersimpan di SQLite.

### 2. Mengubah / Mengedit Produk
1. Cari produk yang ingin diubah pada kartu katalog.
2. Klik tombol **Edit** (warna biru) pada kartu produk tersebut.
3. Form di bagian atas akan otomatis terisi dengan data produk tersebut, dan tombol *Simpan* akan berubah menjadi **Perbarui** (serta muncul tombol **Batal Edit**).
4. Ubah nama, harga, atau foto, lalu klik tombol **Perbarui**.
5. Kartu produk dan database SQLite akan otomatis terupdate.

### 3. Menghapus Produk
1. Cari produk yang ingin dihapus pada katalog.
2. Klik tombol **Hapus** (warna merah) pada kartu produk tersebut.
3. Jendela pop-up konfirmasi akan muncul. Klik **OK** untuk mengonfirmasi penghapusan.
4. Produk akan langsung dihapus dari katalog dan database SQLite.

### 4. Menambahkan Pilihan Gambar Baru
1. Salin file gambar baru berformat `.png` (contoh: `teh.png`) ke dalam folder `src/main/resources/image/`.
2. Buka file `src/main/java/controller/KatalogController.java`.
3. Pada method `initialize()`, tambahkan baris berikut:
   ```java
   fotoBox.getItems().add("teh.png");
   ```
4. Lakukan **Clean and Build** ulang di NetBeans. Opsi `teh.png` sekarang akan tersedia di dropdown foto.

---

## 💻 Teknologi & Dependensi

- **Java**: 17+
- **OpenJFX / JavaFX Controls & FXML**: 21
- **SQLite JDBC Driver**: 3.49.1.0 (`org.xerial:sqlite-jdbc`)
- **JavaFX Maven Plugin**: 0.0.8 (`org.openjfx:javafx-maven-plugin`)

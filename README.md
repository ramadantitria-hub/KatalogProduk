# Katalog Produk (JavaFX + SQLite)

Aplikasi desktop manajemen katalog produk sederhana dengan operasi CRUD (*Create, Read, Update, Delete*) menggunakan **JavaFX** dan database lokal **SQLite**.

---

## Fitur
- **Tambah Produk**: Input nama, harga, dan pilih foto produk.
- **Lihat Katalog**: Menampilkan daftar produk dalam bentuk kartu (*card view*).
- **Edit Produk**: Mengubah data produk yang sudah tersimpan.
- **Hapus Produk**: Menghapus produk dari database dengan konfirmasi.
- **Database SQLite**: Data otomatis tersimpan permanen di `data/katalog.db`.

---

## Cara Menjalankan

### Melalui Apache NetBeans
1. Buka project **`KatalogProduk`** di NetBeans.
2. Klik kanan project > pilih **Clean and Build** (`Shift + F11`).
3. Klik kanan project > pilih **Run** (`F6`).

### Melalui Terminal / Command Line
Buka terminal di dalam folder proyek, lalu jalankan:
```bash
mvn clean javafx:run
```

---

## Teknologi
- **Bahasa**: Java 17+
- **GUI**: JavaFX 21 (FXML & CSS)
- **Database**: SQLite JDBC (3.49.1.0)
- **Build Tool**: Maven

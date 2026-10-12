# Spesifikasi Proyek KASIR ROTA

## 1. Gambaran Umum

KASIR ROTA merupakan proyek latihan pengembangan aplikasi kasir untuk membantu pelaku usaha kecil mencatat produk dan transaksi dengan alur yang sederhana.

Repositori ini digunakan untuk mempelajari proses pengembangan perangkat lunak secara bertahap, mulai dari identifikasi kebutuhan, perencanaan, implementasi, pengujian, evaluasi, hingga perbaikan.

## 2. Permasalahan

Pencatatan transaksi dan stok secara manual dapat menyulitkan pelaku usaha ketika jumlah produk dan transaksi bertambah. Aplikasi kasir diharapkan dapat membantu proses pencatatan menjadi lebih terstruktur.

## 3. Tujuan

1. Menyediakan alur transaksi yang mudah dipahami.
2. Membantu pencatatan produk dan stok.
3. Menghitung total belanja dan kembalian secara tepat.
4. Menyimpan transaksi agar dapat dilihat kembali.
5. Menguji setiap fungsi berdasarkan kasus uji yang terdokumentasi.

## 4. Pengguna Sasaran

Pelaku usaha kecil dan UMKM yang membutuhkan bantuan untuk mencatat produk, transaksi, dan hasil penjualan.

## 5. Alur Inti

Alur transaksi yang direncanakan:

1. Pengguna memilih atau memindai produk.
2. Produk dimasukkan ke keranjang dan jumlahnya ditentukan.
3. Sistem menghitung total belanja.
4. Pengguna memasukkan jumlah uang pembayaran.
5. Sistem memvalidasi pembayaran dan menghitung kembalian.
6. Transaksi disimpan.
7. Transaksi yang tersimpan ditampilkan dalam daftar atau rekap.

Alur ini merupakan spesifikasi awal dan harus diverifikasi melalui implementasi serta pengujian.

## 6. Kebutuhan Fungsional

- Pengelolaan data produk dan harga.
- Pengelolaan jumlah barang dalam keranjang.
- Perhitungan total belanja.
- Validasi jumlah pembayaran.
- Perhitungan kembalian.
- Penyimpanan transaksi.
- Penampilan daftar transaksi yang tersimpan.

## 7. Aturan Bisnis

1. Produk yang ditambahkan harus memiliki data yang valid.
2. Jumlah barang harus berupa bilangan positif.
3. Harga produk tidak boleh bernilai negatif.
4. Total belanja dihitung berdasarkan harga dan jumlah setiap produk.
5. Pembayaran harus sama dengan atau lebih besar daripada total belanja.
6. Kembalian dihitung dari pembayaran dikurangi total belanja.
7. Transaksi hanya disimpan setelah validasi berhasil.

## 8. Persyaratan Minimum Website Challenge

Versi website yang akan dikembangkan harus memiliki:

- Satu alur inti dengan minimal tiga langkah.
- Validasi input pada formulir.
- Perhitungan atau aturan bisnis numerik.
- Penyimpanan data yang tetap tersedia setelah halaman dimuat ulang.
- Daftar atau rekap data yang telah disimpan.

Pemenuhan setiap persyaratan akan diperiksa melalui pengujian.

## 9. Kebutuhan Nonfungsional

- Antarmuka mudah dipahami.
- Pesan kesalahan ditampilkan dengan jelas.
- Data transaksi dapat diperiksa kembali.
- Aplikasi dapat diuji melalui browser.
- Kode dan dokumentasi dikelola melalui GitHub.

## 10. Batasan dan Status

Dokumen ini merupakan spesifikasi awal. Fitur yang direncanakan tidak boleh dianggap sudah berfungsi sebelum implementasi dan pengujiannya berhasil.

Pemilihan teknologi, mekanisme penyimpanan untuk website, serta integrasi dengan aplikasi Flutter akan ditentukan setelah audit proyek dan perencanaan teknis.

## 11. Kriteria Penerimaan

Proyek dinyatakan memenuhi kebutuhan inti apabila:

1. Pengguna dapat menyelesaikan alur transaksi tanpa melewati validasi.
2. Total belanja dan kembalian sesuai perhitungan.
3. Pembayaran yang kurang ditolak.
4. Transaksi berhasil disimpan dan tetap tersedia setelah halaman dimuat ulang.
5. Transaksi tersimpan dapat ditampilkan kembali.

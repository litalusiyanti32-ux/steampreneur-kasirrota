# Spesifikasi Awal KASIR ROTA

## 1. Identitas Proyek

- **Nama produk:** KASIR ROTA
- **Jenis produk:** Website kasir sederhana untuk latihan pengembangan perangkat lunak dengan pendekatan Vibe Engineering.
- **Target pengguna:** Pelaku usaha kecil atau UMKM yang membutuhkan pencatatan transaksi sederhana.
- **Status dokumen:** Spesifikasi awal; belum menjadi bukti bahwa fitur sudah diimplementasikan atau diuji.
- **Repositori:** https://github.com/litalusiyanti32-ux/steampreneur-kasirrota

## 2. Latar Belakang Masalah

Pencatatan transaksi secara manual dapat menyulitkan pelaku usaha ketika jumlah transaksi meningkat. Kesalahan memasukkan jumlah barang, menghitung total belanja, atau menentukan uang kembalian dapat memengaruhi ketepatan pencatatan penjualan.

KASIR ROTA direncanakan sebagai website kasir sederhana yang membantu pengguna mencatat transaksi, menghitung total belanja dan uang kembalian, menyimpan transaksi, serta melihat rekap transaksi yang telah tersimpan.

Pengembangan dilakukan secara bertahap. Setiap fitur perlu diperiksa berdasarkan kebutuhan, aturan bisnis, dan hasil pengujian yang telah ditentukan.

## 3. Riset Pengguna dan Asumsi Awal

### 3.1 Persona sementara

Karena riset langsung kepada calon pengguna belum dilakukan, spesifikasi ini menggunakan persona sementara berdasarkan asumsi yang perlu divalidasi.

**Persona: Pelaku UMKM dengan kebutuhan pencatatan sederhana**

- **Kebutuhan:** Mencatat transaksi dan mengetahui jumlah pembayaran serta uang kembalian dengan benar.
- **Kemungkinan kendala:** Pengguna dapat mengalami kesulitan jika alur transaksi terlalu panjang atau informasi yang ditampilkan kurang jelas.
- **Kebutuhan informasi:** Daftar transaksi yang sudah disimpan agar transaksi sebelumnya dapat ditinjau kembali.
- **Asumsi penggunaan:** Pengguna memiliki akses ke browser pada perangkat yang digunakan untuk menjalankan website.

Persona ini bukan hasil wawancara atau temuan penelitian langsung. Asumsi di atas perlu diperiksa kembali apabila wawancara atau observasi pengguna dapat dilakukan.

## 4. Tujuan Produk

KASIR ROTA versi pertama bertujuan untuk:

1. Menyediakan alur transaksi kasir yang sederhana.
2. Menghitung total transaksi berdasarkan harga dan jumlah barang.
3. Memvalidasi pembayaran sebelum transaksi disimpan.
4. Menghitung uang kembalian dengan benar.
5. Menyimpan transaksi menggunakan `localStorage` pada browser.
6. Menampilkan rekap transaksi yang telah tersimpan.

## 5. Ruang Lingkup Versi Pertama

### 5.1 Fitur yang direncanakan

- Memasukkan data barang yang diperlukan untuk transaksi, berupa nama barang, harga, dan jumlah.
- Menambahkan barang ke daftar transaksi.
- Menghitung subtotal atau total belanja.
- Memasukkan nominal uang pembayaran.
- Menolak pembayaran yang tidak memenuhi ketentuan.
- Menghitung uang kembalian.
- Menyimpan transaksi yang valid ke `localStorage`.
- Menampilkan daftar transaksi yang telah tersimpan.
- Memuat kembali data transaksi yang tersimpan setelah halaman dimuat ulang pada browser yang sama.

### 5.2 Fitur di luar cakupan

Versi pertama tidak mencakup:

- Diskon anggota atau diskon berdasarkan nominal belanja.
- Pengelolaan stok masuk, stok keluar, atau pengurangan stok otomatis.
- Login, akun pengguna, dan pengelolaan hak akses.
- Sinkronisasi data antarp perangkat.
- Penyimpanan terpusat pada server atau database.
- Integrasi pembayaran digital.
- Pemindaian barcode sebagai persyaratan alur utama versi pertama.
- Laporan analitik lanjutan.

Pembatasan ini ditetapkan agar pengembangan berfokus pada satu alur transaksi yang lengkap dan dapat diuji.

## 6. Alur Utama Pengguna

Alur utama yang direncanakan adalah sebagai berikut:

1. Pengguna membuka halaman transaksi.
2. Pengguna memasukkan data barang dan jumlahnya.
3. Website memvalidasi data barang dan menghitung total belanja.
4. Pengguna memasukkan nominal pembayaran.
5. Website memvalidasi pembayaran.
6. Jika pembayaran mencukupi, website menghitung kembalian.
7. Pengguna menyelesaikan transaksi dan website menyimpan transaksi yang valid.
8. Transaksi yang tersimpan muncul pada halaman rekap.
9. Pengguna dapat memuat ulang halaman dan memeriksa apakah transaksi tetap tersedia.

Jika data tidak valid atau pembayaran kurang, website harus menampilkan pesan yang jelas dan tidak menyimpan transaksi tersebut sebagai transaksi berhasil.

## 7. Aturan Bisnis

### 7.1 Data barang

- Nama barang wajib diisi.
- Harga harus berupa angka dan tidak boleh negatif.
- Jumlah barang harus berupa bilangan bulat positif.
- Data yang tidak memenuhi ketentuan harus ditolak dengan pesan yang jelas.

### 7.2 Perhitungan transaksi

Untuk setiap barang:

`Subtotal barang = Harga barang × Jumlah barang`

Untuk seluruh barang dalam transaksi:

`Total transaksi = Jumlah seluruh subtotal barang`

Tidak ada diskon pada versi pertama. Karena itu, total transaksi sama dengan jumlah seluruh subtotal barang.

### 7.3 Validasi pembayaran

- Nominal pembayaran harus berupa angka yang valid dan tidak negatif.
- Pembayaran harus sama dengan atau lebih besar daripada total transaksi.
- Jika pembayaran kurang dari total, website menampilkan pesan **“Uang pembayaran kurang”** dan transaksi tidak boleh disimpan sebagai transaksi berhasil.
- Jika pembayaran mencukupi, kembalian dihitung dengan rumus:

`Kembalian = Nominal pembayaran − Total transaksi`

- Jika pembayaran sama dengan total transaksi, kembalian adalah nol.

### 7.4 Penyimpanan transaksi

- Transaksi hanya boleh disimpan setelah seluruh validasi berhasil.
- Data transaksi yang disimpan harus memuat informasi yang cukup untuk menampilkan rekap, seperti waktu transaksi, daftar barang, jumlah, harga, total transaksi, pembayaran, dan kembalian.
- Data disimpan menggunakan `localStorage` pada browser.
- Setelah halaman dimuat ulang pada browser yang sama, data transaksi yang tersimpan diharapkan masih dapat ditampilkan.
- `localStorage` tidak menjamin sinkronisasi antarp perangkat dan bukan pengganti database server.

## 8. Kebutuhan Fungsional

| ID | Kebutuhan | Kriteria penerimaan |
|---|---|---|
| F-01 | Memasukkan data barang | Nama, harga, dan jumlah divalidasi sebelum digunakan. |
| F-02 | Menghitung total | Total sama dengan jumlah seluruh harga dikalikan jumlah barang. |
| F-03 | Memvalidasi pembayaran | Pembayaran yang kurang ditolak dan menghasilkan pesan yang jelas. |
| F-04 | Menghitung kembalian | Kembalian sama dengan pembayaran dikurangi total transaksi. |
| F-05 | Menyimpan transaksi | Transaksi valid tersimpan setelah pengguna menyelesaikan transaksi. |
| F-06 | Menampilkan rekap | Transaksi yang tersimpan dapat dilihat pada halaman rekap. |
| F-07 | Mempertahankan data | Transaksi tetap tersedia setelah halaman dimuat ulang pada browser yang sama. |

Seluruh kebutuhan di atas masih berstatus **direncanakan** sampai implementasi dan pengujiannya benar-benar dilakukan.

## 9. Kebutuhan Nonfungsional

- Antarmuka menggunakan bahasa yang mudah dipahami.
- Pesan kesalahan menjelaskan data atau tindakan yang perlu diperbaiki.
- Informasi total, pembayaran, dan kembalian mudah dibedakan.
- Alur transaksi tidak memerlukan langkah yang tidak relevan dengan kebutuhan versi pertama.
- Website dapat dijalankan melalui browser dengan mengikuti petunjuk pada README.
- Struktur kode dan dokumentasi cukup jelas untuk ditinjau serta dijelaskan oleh anggota tim.

## 10. Kriteria Penerimaan Produk

Versi pertama dapat dinyatakan memenuhi spesifikasi apabila seluruh kriteria berikut berhasil dibuktikan melalui pengujian:

1. Pengguna dapat menyelesaikan alur transaksi yang terdiri atas minimal tiga langkah.
2. Data barang yang tidak valid ditolak dengan pesan yang jelas.
3. Total transaksi sesuai dengan perhitungan berdasarkan harga dan jumlah barang.
4. Pembayaran yang kurang tidak menghasilkan transaksi berhasil.
5. Pembayaran yang mencukupi menghasilkan kembalian yang benar.
6. Transaksi valid tersimpan pada `localStorage`.
7. Transaksi yang telah disimpan muncul pada rekap.
8. Data transaksi tetap tersedia setelah halaman dimuat ulang pada browser yang sama.
9. Bukti pengujian dapat ditelusuri melalui dokumen kasus uji dan dokumentasi proyek.

Kriteria ini belum dinyatakan lulus sebelum pengujian dilakukan dan hasilnya dicatat.

## 11. Risiko dan Batasan

- **Asumsi kebutuhan pengguna:** Persona belum divalidasi melalui wawancara atau observasi langsung.
- **Penyimpanan lokal:** Data dapat hilang jika penyimpanan browser dihapus atau pengguna berpindah browser/perangkat.
- **Validasi perhitungan:** Hasil perhitungan harus dibandingkan dengan hasil yang diharapkan pada kasus uji.
- **Perubahan kebutuhan:** Fitur tambahan tidak langsung dimasukkan ke versi pertama tanpa mempertimbangkan dampaknya terhadap ruang lingkup dan kasus uji.
- **Bukti implementasi:** Keberadaan dokumen spesifikasi tidak membuktikan bahwa website sudah berjalan.

## 12. Dokumen Terkait

- `docs/02-rencana.md` — rencana tahapan pengembangan.
- `docs/03-log-prompt.md` — catatan prompt, hasil AI, dan tindak lanjut.
- `docs/04-kasus-uji.md` — skenario pengujian, data masukan, dan hasil yang diharapkan.
- `docs/05-kesalahan-ai.md` — catatan kesalahan atau hasil AI yang perlu diperbaiki.
- `docs/06-catatan-review.md` — catatan peninjauan kode dan keputusan pengembangan.
- `docs/07-refleksi.md` — refleksi proses pengembangan.
- `docs/08-penjelasan-kode.md` — penjelasan kode yang benar-benar dibuat dan dipahami tim.

## 13. Status Spesifikasi

Spesifikasi ini menjadi dasar awal pengembangan KASIR ROTA. Keputusan mengenai tidak adanya diskon, belum adanya pengelolaan stok, penggunaan `localStorage`, persona sementara, dan cakupan transaksi telah ditetapkan untuk versi pertama.

**Status implementasi dan pengujian: belum dibuktikan dalam dokumen ini.**

Sebelum Checkpoint 1, spesifikasi perlu diselaraskan dengan kasus uji dan rencana pengerjaan. Nilai hasil perhitungan yang diharapkan harus diperiksa terlebih dahulu dan setiap asumsi harus tetap ditandai sebagai asumsi sampai ada bukti pendukung.

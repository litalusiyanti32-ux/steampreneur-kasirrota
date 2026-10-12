# Kasus Uji KASIR ROTA

## 1. Tujuan Pengujian

Dokumen ini berisi skenario untuk memeriksa apakah KASIR ROTA memenuhi spesifikasi versi pertama, khususnya perhitungan transaksi, validasi pembayaran, penyimpanan menggunakan `localStorage`, dan tampilan rekap.

Dokumen ini merupakan rencana pengujian. Status setiap kasus tetap **Belum diuji** sampai pengujian benar-benar dilakukan.

## 2. Data Uji

| Barang | Harga | Jumlah | Subtotal |
|---|---:|---:|---:|
| Teh | Rp5.000 | 2 | Rp10.000 |
| Roti | Rp8.000 | 1 | Rp8.000 |
| **Total transaksi** | | | **Rp18.000** |

Data di atas merupakan data simulasi untuk pengujian, bukan data transaksi pengguna nyata.

## 3. Skenario Pengujian

| ID | Skenario | Masukan atau tindakan | Hasil yang diharapkan | Status |
|---|---|---|---|---|
| KU-01 | Transaksi normal | Teh 2 buah dan roti 1 buah; pembayaran Rp20.000 | Total Rp18.000, kembalian Rp2.000, transaksi dapat disimpan | Belum diuji |
| KU-02 | Pembayaran pas | Total Rp18.000; pembayaran Rp18.000 | Transaksi dapat disimpan dan kembalian Rp0 | Belum diuji |
| KU-03 | Pembayaran kurang | Total Rp18.000; pembayaran Rp17.999 | Pesan “Uang pembayaran kurang”; transaksi tidak disimpan sebagai transaksi berhasil | Belum diuji |
| KU-04 | Pembayaran nol | Total Rp18.000; pembayaran Rp0 | Pembayaran ditolak dan transaksi tidak disimpan sebagai transaksi berhasil | Belum diuji |
| KU-05 | Nama barang kosong | Nama barang tidak diisi | Data ditolak dan pesan validasi ditampilkan | Belum diuji |
| KU-06 | Harga negatif | Harga barang -Rp1.000 | Data ditolak | Belum diuji |
| KU-07 | Harga bukan angka | Harga diisi teks yang tidak dapat diproses sebagai angka | Data ditolak dengan pesan yang jelas | Belum diuji |
| KU-08 | Jumlah nol | Jumlah barang 0 | Data ditolak karena jumlah harus positif | Belum diuji |
| KU-09 | Jumlah pecahan | Jumlah barang 1,5 | Data ditolak karena jumlah harus berupa bilangan bulat | Belum diuji |
| KU-10 | Keranjang kosong | Pengguna mencoba menyelesaikan transaksi tanpa barang | Transaksi ditolak dan tidak disimpan | Belum diuji |
| KU-11 | Rekap transaksi | Satu transaksi berhasil disimpan | Transaksi muncul pada daftar rekap dengan informasi yang sesuai | Belum diuji |
| KU-12 | Data setelah reload | Simpan transaksi, lalu muat ulang halaman | Transaksi tetap muncul pada browser yang sama | Belum diuji |
| KU-13 | Transaksi gagal tidak tersimpan | Lakukan transaksi dengan pembayaran kurang | Transaksi gagal tidak muncul sebagai transaksi berhasil pada rekap | Belum diuji |

## 4. Pemeriksaan Perhitungan

Perhitungan acuan untuk KU-01:

- Subtotal teh: Rp5.000 × 2 = Rp10.000
- Subtotal roti: Rp8.000 × 1 = Rp8.000
- Total transaksi: Rp10.000 + Rp8.000 = Rp18.000
- Pembayaran: Rp20.000
- Kembalian: Rp20.000 − Rp18.000 = Rp2.000

Perhitungan acuan untuk KU-02:

- Total transaksi: Rp18.000
- Pembayaran: Rp18.000
- Kembalian: Rp18.000 − Rp18.000 = Rp0

Perhitungan acuan untuk KU-03:

- Total transaksi: Rp18.000
- Pembayaran: Rp17.999
- Selisih kekurangan: Rp18.000 − Rp17.999 = Rp1

Karena pembayaran kurang Rp1, transaksi harus ditolak.

## 5. Pengujian Penyimpanan

Pemeriksaan penyimpanan dilakukan setelah fitur transaksi tersedia.

1. Jalankan website melalui cara yang ditentukan pada README.
2. Buat satu transaksi dengan data uji.
3. Pastikan transaksi berhasil disimpan.
4. Buka bagian rekap dan cocokkan informasi transaksi.
5. Muat ulang halaman.
6. Periksa apakah transaksi yang sama tetap tersedia.
7. Catat hasil sebenarnya dan dokumentasikan bukti jika diperlukan.

Pengujian ini hanya memeriksa penyimpanan lokal pada browser yang sama. Pengujian belum membuktikan sinkronisasi antarp perangkat atau penyimpanan server.

## 6. Pencatatan Hasil

Status pengujian yang digunakan:

- **Belum diuji:** peng

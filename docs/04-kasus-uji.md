# Kasus Uji KASIR ROTA

## 1. Tujuan

Dokumen ini menetapkan skenario pengujian untuk memeriksa fungsi utama aplikasi kasir. Hasil pengujian harus dicatat berdasarkan perilaku aplikasi yang benar-benar diamati.

## 2. Daftar Kasus Uji

| ID | Skenario | Langkah Pengujian | Hasil yang Diharapkan |
|---|---|---|---|
| TC-01 | Transaksi normal | Pilih produk, tentukan jumlah, lalu masukkan pembayaran yang cukup | Total dan kembalian dihitung dengan benar, transaksi tersimpan |
| TC-02 | Pembayaran kurang | Masukkan pembayaran di bawah total belanja | Transaksi ditolak dan pesan yang sesuai ditampilkan |
| TC-03 | Jumlah barang tidak valid | Masukkan jumlah nol atau negatif | Input ditolak |
| TC-04 | Harga tidak valid | Masukkan harga negatif | Input ditolak |
| TC-05 | Perhitungan total | Tambahkan beberapa produk dengan jumlah berbeda | Total sama dengan penjumlahan harga dikali jumlah setiap produk |
| TC-06 | Perhitungan kembalian | Masukkan pembayaran lebih besar daripada total | Kembalian sama dengan pembayaran dikurangi total |
| TC-07 | Penyimpanan transaksi | Selesaikan transaksi, lalu muat ulang halaman | Transaksi tetap tersedia |
| TC-08 | Rekap transaksi | Buka daftar transaksi setelah menyimpan transaksi | Transaksi yang tersimpan ditampilkan dengan data yang sesuai |

## 3. Pencatatan Hasil

Setiap kasus uji harus dicatat menggunakan status berikut:

- **LULUS**: hasil aktual sesuai dengan hasil yang diharapkan.
- **GAGAL**: hasil aktual tidak sesuai dengan hasil yang diharapkan.
- **BELUM DIUJI**: pengujian belum dijalankan.

## 4. Format Catatan Pengujian

Untuk setiap pengujian, catat:

- ID kasus uji.
- Tanggal pengujian.
- Kondisi awal.
- Langkah yang dijalankan.
- Hasil yang diharapkan.
- Hasil aktual.
- Status pengujian.
- Bukti pengujian jika tersedia.

## 5. Catatan

Dokumen ini merupakan rencana pengujian awal. Semua hasil tetap berstatus BELUM DIUJI sampai pengujian dilakukan. Jika implementasi memiliki perilaku yang berbeda, catat hasil aktual dan evaluasi apakah kode atau spesifikasinya perlu diperbaiki.

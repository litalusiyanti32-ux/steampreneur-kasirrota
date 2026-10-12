# Rencana Pengembangan KASIR ROTA

## 1. Tujuan

Rencana ini menjadi panduan pengerjaan KASIR ROTA secara bertahap dengan pendekatan Vibe Engineering. Setiap tahap mencakup pekerjaan, hasil yang diharapkan, dan pemeriksaan sebelum melanjutkan ke tahap berikutnya.

Estimasi waktu merupakan perkiraan awal dan dapat disesuaikan berdasarkan hasil pengerjaan. Status pekerjaan tidak dianggap selesai sebelum ada bukti yang sesuai.

## 2. Tahapan Pengerjaan

| Tahap | Pekerjaan | Hasil yang diharapkan | Estimasi |
|---|---|---|---|
| 1 | Menentukan kebutuhan dan persona pengguna | Kebutuhan, masalah, dan asumsi awal tercatat dalam spesifikasi | 30 menit |
| 2 | Menyelesaikan spesifikasi dan kasus uji | Aturan bisnis, ruang lingkup, data uji, dan hasil yang diharapkan tersedia | 45 menit |
| 3 | Menyusun rencana pengembangan | Urutan pengerjaan, estimasi waktu, dan risiko terdokumentasi | 20 menit |
| 4 | Memeriksa konsistensi dokumen dan membuat Checkpoint 1 | Spesifikasi, kasus uji, dan rencana siap menjadi acuan implementasi | 10 menit |
| 5 | Membuat struktur website dan alur transaksi awal | Website dapat dijalankan dan alur transaksi mulai dibangun | 60 menit |
| 6 | Menambahkan validasi dan perhitungan | Validasi input, total transaksi, pembayaran, dan kembalian tersedia | 60 menit |
| 7 | Menambahkan penyimpanan dan rekap | Transaksi valid tersimpan dan dapat ditampilkan kembali | 60 menit |
| 8 | Menguji dan memperbaiki alur inti | Kasus uji dijalankan dan hasilnya dicatat | 45 menit |
| 9 | Memeriksa pemahaman dan kualitas kode | Catatan review dan penjelasan kode sesuai implementasi sebenarnya | 45 menit |
| 10 | Membuat Checkpoint 2 | Versi pertama alur inti telah diperiksa dan siap ditandai sebagai checkpoint | 10 menit |
| 11 | Menganalisis Change Request | Dampak fitur pencarian, filter, dan ekspor CSV dicatat sebelum perubahan kode | 30 menit |
| 12 | Mengimplementasikan Change Request | Fitur tambahan diterapkan tanpa merusak alur inti | 60 menit |
| 13 | Menguji kembali dan menyiapkan bukti | Hasil pengujian terbaru dan bukti tangkapan layar tersedia | 45 menit |
| 14 | Menyiapkan dokumentasi dan akses juri | README, petunjuk menjalankan website, struktur folder, dan bukti lengkap | 45 menit |
| 15 | Menyelesaikan Bug Hunt | Bug diperiksa dan diperbaiki mengikuti aturan serta batas waktu challenge | 60 menit khusus sesi Bug Hunt |
| 16 | Menyusun refleksi dan pemeriksaan akhir | Refleksi, keterbatasan, dan kesiapan repositori dicatat | 30 menit |

Estimasi tersebut adalah rencana awal, bukan durasi yang sudah digunakan. Waktu Bug Hunt harus mengikuti jadwal resmi challenge dan tidak boleh dimulai jika waktu yang tersedia tidak mencukupi.

## 3. Urutan Pengembangan Website

Versi pertama akan dibangun menggunakan teknologi web yang dapat dijalankan melalui browser.

Urutan implementasi:

1. Menyiapkan struktur berkas website.
2. Membuat antarmuka transaksi sederhana.
3. Membuat input nama barang, harga, dan jumlah.
4. Menghitung subtotal dan total transaksi.
5. Memvalidasi data dan nominal pembayaran.
6. Menghitung uang kembalian.
7. Menyimpan transaksi valid menggunakan `localStorage`.
8. Menampilkan daftar transaksi tersimpan.
9. Memeriksa data setelah halaman dimuat ulang.
10. Menjalankan kasus uji dan memperbaiki masalah yang ditemukan.

Pengerjaan dilakukan secara bertahap. Setiap perubahan perlu diperiksa sebelum fitur berikutnya ditambahkan.

## 4. Fitur Opsional: Barcode Scanner

Barcode scanner tidak menjadi persyaratan wajib versi pertama.

Setelah alur inti website berjalan, kelayakan pemindaian barcode melalui kamera browser akan diperiksa. Jika dapat diterapkan dengan baik tanpa mengganggu penyelesaian alur inti, fitur tersebut dapat ditambahkan sebagai pengembangan lanjutan.

Jika mengalami kendala atau berisiko menghambat penyelesaian website, pengerjaan tetap dilanjutkan tanpa barcode scanner. Keberhasilan fitur barcode pada aplikasi Flutter tidak dianggap sebagai bukti bahwa fitur yang sama telah berjalan pada website.

## 5. Strategi Pengujian

Pengujian dilakukan berdasarkan `docs/04-kasus-uji.md`.

Pemeriksaan mencakup:

- Transaksi normal dengan hasil perhitungan yang diketahui.
- Pembayaran pas dan pembayaran lebih.
- Pembayaran kurang.
- Input barang yang tidak valid.
- Keranjang kosong.
- Penyimpanan transaksi.
- Tampilan rekap.
- Ketahanan data setelah halaman dimuat ulang.
- Pengujian ulang setelah perbaikan atau perubahan fitur.

Setiap kasus dicatat dengan status aktual. Jika ditemukan kegagalan, penyebab dan tindak lanjut didokumentasikan sebelum menyatakan kasus tersebut lulus.

## 6. Checkpoint

### Checkpoint 1

Checkpoint 1 dibuat setelah:

- `docs/01-spesifikasi.md` lengkap.
- `docs/04-kasus-uji.md` lengkap dan hasil perhitungan yang diharapkan sudah diperiksa.
- `docs/02-rencana.md` lengkap.
- Ketiga dokumen konsisten satu sama lain.

Pesan commit yang digunakan:

`checkpoint: spesifikasi, kasus uji, dan rencana selesai`

Kode website belum menjadi bagian dari checkpoint ini.

### Checkpoint 2

Checkpoint 2 dibuat setelah versi pertama alur inti berhasil dijalankan dan diperiksa berdasarkan kasus uji yang relevan.

Pesan commit yang digunakan:

`checkpoint: versi pertama alur inti berjalan`

Change Request baru dikerjakan setelah Checkpoint 2.

## 7. Change Request

Change Request mencakup penambahan:

- Pencarian data transaksi.
- Filter data transaksi.
- Ekspor data ke format CSV.

Sebelum mengubah kode, analisis terlebih dahulu dampak perubahan terhadap struktur data, tampilan rekap, alur inti, dan kasus uji. Hasil analisis dicatat dalam `docs/analisis-change-request.md`.

Setelah implementasi, jalankan kembali kasus uji alur inti untuk memeriksa apakah fitur sebelumnya tetap berfungsi.

## 8. Bug Hunt

Bug Hunt dilaksanakan sebagai sesi terpisah sesuai ketentuan challenge.

- Jangan membuka atau memodifikasi kode Bug Hunt sebelum sesi resmi dimulai.
- Periksa batas waktu dan pastikan tersedia waktu pengerjaan yang cukup.
- Pertahankan salinan kode asli sesuai ketentuan challenge.
- Perbaiki masalah satu per satu dan catat setiap perubahan.
- Jalankan pengujian yang disediakan untuk memeriksa perilaku sebelum dan sesudah perbaikan.
- Simpan catatan bug, hasil pengujian, dan commit sesuai aturan challenge.

Bug Hunt tidak boleh dianggap selesai hanya karena kode telah diubah; perbaikan harus didukung hasil pengujian.

## 9. Dokumentasi dan Kesiapan Juri

Dokumentasi akhir direncanakan mencakup:

- Nama dan deskripsi produk.
- Penjelasan alur inti.
- Prasyarat dan petunjuk menjalankan website.
- Struktur folder.
- Perintah pengujian serta hasil yang diharapkan.
- Fitur yang tersedia dan keterbatasannya.
- Tangkapan layar setiap langkah alur inti.
- Tangkapan layar fitur Change Request.
- Sumber dan lisensi yang digunakan.
- Nama anggota tim dan peran masing-masing sesuai ketentuan challenge.
- Penjelasan kode dan refleksi berdasarkan pekerjaan yang benar-benar dilakukan.

Jika dibutuhkan untuk penilaian, siapkan cara agar juri dapat membuka demo website. Jangan menyatakan demo online tersedia sebelum URL benar-benar dapat diakses.

## 10. Risiko dan Penanganan

| Risiko | Penanganan |
|---|---|
| Waktu pengerjaan terbatas | Prioritaskan alur inti dan tunda fitur opsional. |
| Fitur tidak sesuai dengan teknologi web | Uji kelayakan lebih dahulu sebelum memasukkan fitur ke cakupan wajib. |
| Hasil AI tidak sesuai kebutuhan | Periksa kode, jalankan pengujian, dan catat perubahan yang diperlukan. |
| Perubahan merusak fitur sebelumnya | Jalankan kembali kasus uji setelah perubahan. |
| Data lokal tidak tersedia di perangkat lain | Jelaskan batasan `localStorage` pada README. |
| Website belum bisa dibuka oleh juri | Uji petunjuk menjalankan website dan akses demo sebelum menyatakan siap. |
| Bug Hunt menghabiskan waktu tahap utama | Jadwalkan sesi terpisah sesuai aturan challenge. |

## 11. Status Rencana

Rencana ini merupakan panduan awal. Setiap tahap akan diperbarui sesuai pekerjaan yang benar-benar dilakukan.

Status implementasi, pengujian, checkpoint, dan akses demo harus didasarkan pada bukti. Tidak ada fitur yang dinyatakan selesai hanya karena sudah tercantum dalam rencana.

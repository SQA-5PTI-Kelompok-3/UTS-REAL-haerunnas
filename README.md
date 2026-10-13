# Software Quality Assurance — Code Review

- **Nama:** Haerunnas
- **NIM:** 12409011030053

## 1. Code Review Manual — Studi Kasus John Travolta

### 1.1 Deskripsi Kasus

Bagian ini mendokumentasikan pelaksanaan code review manual terhadap program perhitungan gaji mingguan dan tabungan John Travolta. Pemeriksaan dilakukan dengan membaca kode sumber, mencocokkan implementasi dengan ketentuan soal, serta menguji program menggunakan beberapa variasi input.

Ketentuan perhitungan yang digunakan adalah:

- Jam kerja normal maksimal 40 jam per minggu.
- Tarif kerja normal sebesar Rp15.000 per jam.
- Jam kerja yang melebihi 40 jam dibayar dengan tarif lembur sebesar 1,5 kali tarif normal.
- Jika pemasukan lebih besar daripada pengeluaran, program menampilkan status "Bisa menabung".
- Jika pemasukan sama dengan pengeluaran, program menampilkan status "Tidak bisa menabung".
- Jika pemasukan lebih kecil daripada pengeluaran, program menampilkan status "Cari tambahan".

### 1.2 Metodologi Pemeriksaan

Pemeriksaan dilakukan secara manual melalui tahapan berikut:

1. Memahami kebutuhan dan aturan perhitungan pada soal.
2. Memeriksa logika perhitungan gaji normal dan lembur.
3. Memeriksa kondisi perbandingan pemasukan dan pengeluaran.
4. Menjalankan program menggunakan beberapa skenario input.
5. Membandingkan hasil aktual dengan hasil yang diharapkan.
6. Mencatat temuan dan menyusun rekomendasi perbaikan.

### 1.3 Hasil Pemeriksaan dan Pengujian

Pemeriksaan menunjukkan bahwa logika utama perhitungan gaji telah sesuai dengan ketentuan soal untuk input yang valid. Program membedakan jam kerja normal dan lembur, menghitung upah lembur menggunakan tarif 1,5 kali tarif normal, serta menjumlahkan kedua komponen untuk memperoleh total gaji.

Logika penentuan tabungan juga telah sesuai dengan ketentuan. Program membandingkan pemasukan dengan pengeluaran untuk menentukan status keuangan John Travolta.

Salah satu skenario pengujian menggunakan 52 jam kerja dan pengeluaran sebesar Rp600.000. Hasil perhitungannya adalah:

- Gaji normal: 40 × Rp15.000 = Rp600.000.
- Jam lembur: 52 − 40 = 12 jam.
- Tarif lembur: 1,5 × Rp15.000 = Rp22.500 per jam.
- Gaji lembur: 12 × Rp22.500 = Rp270.000.
- Total gaji: Rp600.000 + Rp270.000 = Rp870.000.
- Tabungan: Rp870.000 − Rp600.000 = Rp270.000.

Dengan demikian, status keuangan yang diharapkan adalah "Bisa menabung" dengan jumlah tabungan Rp270.000.

### 1.4 Temuan Code Review

Pemeriksaan kode menghasilkan beberapa temuan yang dapat diperbaiki.

| No. | Bagian yang diperiksa | Temuan | Dampak | Rekomendasi |
|---|---|---|---|---|
| 1 | Validasi jam kerja | Program belum memvalidasi jam kerja negatif dan tidak menangani input nonbilangan bulat dengan baik. | Input tidak valid dapat menghasilkan perhitungan yang tidak masuk akal atau menyebabkan program berhenti dengan error. | Tambahkan validasi agar jam kerja berupa bilangan bulat nonnegatif. |
| 2 | Validasi pengeluaran | Program belum memvalidasi pengeluaran negatif dan mengasumsikan input selalu berupa bilangan bulat. | Input yang tidak valid dapat menghasilkan status keuangan yang tidak sesuai atau menyebabkan program berhenti dengan error. | Tambahkan validasi pengeluaran sebelum melakukan perbandingan dengan pemasukan. |
| 3 | Output kondisi keuangan | Ketika pengeluaran melebihi pemasukan, program hanya menampilkan status "Cari tambahan" tanpa menunjukkan jumlah kekurangan uang. Jumlah tabungan juga hanya ditampilkan jika nilainya lebih besar dari nol. | Informasi keuangan yang ditampilkan menjadi kurang lengkap. | Tampilkan jumlah kekurangan uang dan pertimbangkan untuk selalu menampilkan jumlah tabungan, termasuk Rp0. |

### 1.5 Kesimpulan Code Review Manual

Berdasarkan pemeriksaan yang dilakukan, logika utama program perhitungan gaji dan tabungan John Travolta telah sesuai dengan ketentuan soal untuk input yang valid. Program dapat menghitung gaji normal, upah lembur, total gaji, dan status keuangan berdasarkan perbandingan pemasukan dengan pengeluaran.

Meskipun demikian, terdapat beberapa aspek yang perlu diperbaiki, terutama validasi input jam kerja dan pengeluaran serta kelengkapan informasi pada output. Penambahan validasi dapat mencegah pemrosesan input yang tidak sesuai, sedangkan penyempurnaan output dapat membantu pengguna memahami kondisi keuangannya secara lebih jelas.

## 2. Code Review Menggunakan Dataset CROP

Bagian ini membahas pemeriksaan code review menggunakan dataset CROP (*Code Review Open Platform*), yang menghubungkan informasi proses code review dengan perubahan kode sumber perangkat lunak.

### 2.1 Sumber Dataset

Dataset yang digunakan berasal dari proyek CROP, yang menyediakan data code review beserta informasi pendukungnya.

- **Website resmi:** https://crop-repo.github.io/
- **Repository dataset:** https://github.com/crop-repo/crop
- **Proyek yang diperiksa:** `testrunner`
- **Bahasa pemrograman:** Python

Dataset CROP digunakan sebagai sumber untuk mengidentifikasi perubahan yang diperiksa dan menelusuri konteks proses review. Analisis dilakukan berdasarkan data yang tersedia dan bukti yang berhasil diperiksa.

### 2.2 Objek Code Review

Objek pemeriksaan yang dipilih adalah Review #3622 pada proyek `testrunner`.

| Informasi | Keterangan |
|---|---|
| Nomor review | 3622 |
| Proyek | `testrunner` |
| Bahasa pemrograman | Python |
| Deskripsi perubahan | Minor cleanups |
| Pengaju perubahan | Dustin Sallings |
| Tanggal pengajuan | 11 November 2010 |
| Status review | Merged |
| Branch | `master` |
| Bagian kode yang diperiksa | Fungsi `get_server_info()` pada file `testrunner` |

Halaman review asli dapat diakses melalui tautan berikut:

https://review.couchbase.org/#/c/3622/

### 2.3 Metodologi Pemeriksaan

Pemeriksaan code review dilakukan melalui beberapa tahapan berikut.

1. **Identifikasi metadata:** memeriksa informasi review untuk menentukan identitas perubahan, proyek, status, dan revisi yang dianalisis.
2. **Pemeriksaan diskusi:** menelaah deskripsi perubahan dan informasi aktivitas review untuk memahami konteks perubahan.
3. **Pemeriksaan source code:** membandingkan implementasi sebelum dan sesudah revisi melalui tampilan *code diff*.
4. **Analisis perubahan:** mengevaluasi perubahan logika, pemetaan nilai, dan kemungkinan perbedaan perilaku program.
5. **Pencatatan temuan:** mendokumentasikan hasil pemeriksaan, potensi masalah, dampak yang mungkin terjadi, dan rekomendasi pemeriksaan lanjutan.

Hasil analisis dibedakan antara perubahan yang dapat diamati secara langsung, potensi masalah yang masih membutuhkan verifikasi, dan bug yang telah didukung oleh bukti yang memadai.

### 2.4 Ringkasan Hasil Pemeriksaan

Pemeriksaan Review #3622 berfokus pada fungsi `get_server_info()`, yang digunakan untuk memperoleh informasi sistem operasi, versi, arsitektur, dan ekstensi paket instalasi server.

Perubahan utama yang diamati adalah penyederhanaan pemetaan sistem operasi dan arsitektur. Implementasi sebelumnya menggunakan beberapa kondisi `if` dan `elif`, sedangkan implementasi baru menggunakan struktur data *dictionary* dan metode `.get()`.

Pada kasus yang diperiksa, pemetaan ekstensi untuk Ubuntu, CentOS, Red Hat, dan MacOSX serta pemetaan arsitektur `i686`, `i386`, dan `x86_64` menghasilkan nilai yang sama.

Pemeriksaan juga mengidentifikasi perbedaan dalam penanganan arsitektur yang tidak tercantum secara eksplisit. Implementasi sebelumnya mempertahankan nilai awal `unknown`, sedangkan implementasi baru mempertahankan nilai arsitektur yang diterima. Perbedaan ini dicatat sebagai potensi masalah yang perlu diverifikasi lebih lanjut, bukan sebagai bug yang telah terkonfirmasi.

Halaman review asli menunjukkan bahwa perubahan telah memperoleh persetujuan dan berstatus *Merged*. Namun, halaman tersebut menampilkan keterangan `No comments`, sehingga tidak tersedia komentar diskusi yang dapat digunakan untuk membandingkan temuan pemeriksaan dengan pembahasan reviewer secara langsung.

### 2.5 Kesimpulan Code Review CROP

Penggunaan dataset CROP memungkinkan pemeriksaan code review dilakukan dengan menghubungkan metadata perubahan, informasi aktivitas review, dan perbandingan kode sumber.

Pada Review #3622, perubahan yang diperiksa terutama menyederhanakan implementasi pemetaan sistem operasi dan arsitektur. Meskipun pemetaan untuk kasus yang diperiksa tetap menghasilkan nilai yang sama, terdapat perbedaan penanganan arsitektur yang tidak dikenal dan memerlukan pemeriksaan lanjutan.

Hasil ini menunjukkan pentingnya mengevaluasi perubahan kode tidak hanya dari segi keringkasan implementasi, tetapi juga dari kemungkinan perubahan perilaku program. Seluruh kesimpulan didasarkan pada kode dan informasi review yang telah diperiksa.

## Referensi

1. Paixao, M., et al. *CROP: Linking Code Reviews to Source Code Changes*. Informasi publikasi dan dataset tersedia melalui https://crop-repo.github.io/.
2. CROP Repository. https://github.com/crop-repo/crop
3. Couchbase Code Review, Review #3622. https://review.couchbase.org/#/c/3622/
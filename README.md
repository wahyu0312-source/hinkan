Password Mode Admin (untuk tombol "Admin/管理" di Dashboard, Quality, dll): Kode: admin2025

Password Halaman Forms (untuk membuka kunci halaman forms.html): Kode: kensa2025


📖 Panduan Penentuan Namespace & Prefix

Dokumen ini menjelaskan cara menentukan kode inisial (Namespace dan Prefix) untuk sistem Serial Number Generator (Admin Prefix & GAS). Penamaan yang rapi sangat penting agar data tidak tertukar antar proyek atau departemen.

1. Konsep Dasar

Sistem ini menyimpan data counter (nomor urut) di Google Cloud menggunakan format kunci gabungan:

NAMESPACE + :: + PREFIX

Komponen

Penjelasan

Contoh

NAMESPACE (NS)

Kode untuk Grup Proyek, Departemen, atau Nama Pabrik. Digunakan untuk memisahkan data agar tidak bentrok jika ada Prefix yang sama di proyek berbeda.

okuma, kensa, qc

PREFIX

Kode unik untuk Barang/Model tertentu. Ini adalah teks yang akan muncul di awal nomor seri.

2825-, MB46-, A-

KEY (Otomatis)

Gabungan yang disimpan di Server (GAS).

okuma::2825-

2. Cara Menentukan Nama (Best Practice)

A. Menentukan Namespace (NS)

Namespace sebaiknya bersifat LUAS. Jangan terlalu spesifik.

✅ Gunakan: Nama Customer, Nama Departemen, atau Kode Proyek Besar.

❌ Hindari: Nama orang, tanggal, atau kode yang berubah-ubah tiap bulan.

Aturan Penulisan: Huruf kecil semua, tanpa spasi (gunakan _ jika perlu).

Contoh:

Untuk proyek Okuma: okuma

Untuk departemen QC: qc_dept

Untuk pabrik area casting: casting

B. Menentukan Prefix

Prefix diambil dari Kode Barang atau Tipe Model yang tertera di drawing/dokumen.

Penting: Sertakan tanda pemisah seperti strip (-) di akhir jika ingin ada jarak dengan nomor urut.

Aturan Penulisan: Huruf Besar (Uppercase) agar mudah dibaca operator.

Contoh:

Barang "Cover Y-Axis 2825": Prefix 2825- (Hasil: 2825-001)

Barang "Unit Test A": Prefix UNIT-A- (Hasil: UNIT-A-001)

Laporan Claim: Prefix CLM (Hasil: CLM001 - tanpa strip)

3. Studi Kasus (Contoh Penerapan)

Berikut adalah contoh cara mengisi data di halaman Admin berdasarkan situasi nyata di pabrik.

Kasus 1: Produksi Part Mesin

Kita akan membuat nomor seri untuk part "Y-Axis Cover MB46V" dengan kode drawing 2825-20. Kita ingin nomor serinya 3 digit (001).

NS: okuma (Karena ini pesanan Okuma)

Prefix: 2825- (Diambil dari 4 digit awal kode drawing)

Digits: 3

Start/Next: 1

Hasil Serial Number: 2825-001, 2825-002, dst.

Kasus 2: Nomor Laporan (Dokumen)

Kita butuh nomor unik untuk setiap form claim yang dibuat user.

NS: system (Karena ini internal sistem)

Prefix: RPT- (Singkatan Report)

Digits: 6 (Agar muat banyak, misal 000001)

Start/Next: 1

Hasil Serial Number: RPT-000001, RPT-000002, dst.

4. Cara Setting di Halaman Admin

Setelah Anda menentukan nama di atas kertas, masukkan ke sistem:

Buka halaman Admin Prefix (admin-prefix.html).

Lihat kotak Server (GAS) di sebelah kanan.

Masukkan NS dan Prefix yang sudah ditentukan.

Contoh NS: okuma

Contoh Prefix: 2825-

Tentukan jumlah digit (misal 3) dan nomor awal (1).

Klik tombol Set Digits → Tunggu notifikasi "OK".

Klik tombol Set Next → Tunggu notifikasi "OK".

Selesai. Server sudah mengenali kode barang tersebut.

5. Cara Penggunaan oleh Operator

Operator tidak perlu memikirkan NS. Mereka hanya perlu memasukkan "Kunci Lengkap" di komputer mereka.

Operator membuka admin-prefix.html di komputer kerja mereka.

Di kotak Local Override, masukkan format gabungan: ns::prefix.

Input: okuma::2825-

Klik Save Local.

Sekarang komputer tersebut sudah "terkunci" untuk mencetak nomor seri 2825-.

📋 Cheat Sheet (Format)

Input Field

Format Ideal

Contoh Salah

Contoh Benar

Namespace

[a-z0-9_] (Kecil, tanpa spasi)

Okuma Jaya

okuma

Prefix

[A-Z0-9-] (Besar, boleh simbol)

part 1

PART-1-

Local Key

ns::prefix

2825-

okuma::2825-

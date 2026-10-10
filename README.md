# Dataset Kuliah Big Data, AI, and Coding

Kumpulan data latihan untuk praktikum mata kuliah **Big Data, AI, and Coding**. Semua data bersifat **fiktif** dan dibuat khusus untuk pembelajaran. Nama orang di dalamnya dibuat acak dan tidak merujuk siapa pun.

Ada dua tema yang bisa dipilih. Keduanya mengikuti alur yang sama: membaca data, memvisualisasikan, membuat dasbor, lalu memprediksi.

| Tema | File | Jumlah baris | Pertemuan |
|---|---|---|---|
| Toko kopi | `transaksi_toko_kopi.csv` | 1.560 | 3–5 |
| Toko kopi | `pelanggan_toko_kopi.csv` | 600 | 6–7 |
| Sekolah | `nilai_siswa.csv` | 3.600 | 3–5 |
| Sekolah | `profil_belajar_siswa.csv` | 360 | 6–7, 10 |
| Sekolah | `umpan_balik_siswa.csv` | 300 | 9 |

## Cara memakai

**Python (Pandas / Google Colab)**

```python
import pandas as pd

url = "https://raw.githubusercontent.com/irzal/dataset-kuliah/refs/heads/main/nilai_siswa.csv"
df = pd.read_csv(url)
df.head()
```

Ganti nama file di akhir URL untuk membuka data lain.

**Google Data Studio:** unduh file CSV (tombol *Download raw file*), lalu tambahkan sebagai sumber data lewat *File Upload*. Bisa juga impor dulu ke Google Sheets.

**Orange:** unduh file CSV, lalu buka dengan widget *File*. Atur kolom target sebagai *target* di jendela pengaturan kolom.

---

## Tema 1: Toko Kopi

### transaksi_toko_kopi.csv
Transaksi sebuah kedai kopi selama satu minggu (28 September – 4 Oktober 2026). Satu baris = satu transaksi.

| Kolom | Keterangan |
|---|---|
| ID_Transaksi | Kode unik transaksi |
| Tanggal, Jam | Waktu transaksi |
| Nama_Menu | Nama minuman yang dibeli |
| Kategori | Kopi atau Non-Kopi |
| Harga | Harga satuan (Rupiah) |
| Metode_Bayar | Cara pembayaran |
| Banyak | Jumlah gelas |
| Total_Bayar | Harga × Banyak |

### pelanggan_toko_kopi.csv
Profil 600 pelanggan kedai kopi. Satu baris = satu pelanggan.

| Kolom | Keterangan |
|---|---|
| ID_Pelanggan | Kode unik pelanggan |
| Usia | Umur pelanggan |
| Member | Ya / Tidak |
| Frekuensi_Kunjungan | Banyak kunjungan |
| Total_Belanja | Total belanja (Rupiah) |
| Hari_Libur | Biasa datang di hari libur (Ya / Tidak) |
| Hari_Sejak_Kunjungan_Terakhir | Jarak hari sejak terakhir datang |
| Pakai_Promo | Ya / Tidak |
| Menu_Favorit | Menu yang paling sering dipesan |
| Metode_Bayar | Cara bayar yang paling sering dipakai |
| **Status** | **Target**: Kembali (429) atau Kabur (171) |

---

## Tema 2: Sekolah (Nilai Siswa)

Data sebuah SMP fiktif dengan 12 rombongan belajar (kelas VII-1 sampai IX-4), 360 siswa, 5 mata pelajaran, dan 2 semester. Ketiga file bisa digabung lewat kolom `NIS`.

### nilai_siswa.csv
Satu baris = nilai satu siswa untuk satu mata pelajaran dalam satu semester.

| Kolom | Keterangan |
|---|---|
| ID_Nilai | Kode unik baris nilai |
| NIS | Nomor induk siswa |
| Nama | Nama siswa (fiktif) |
| Jenis_Kelamin | L / P |
| Kelas | VII-1 sampai IX-4 |
| Semester | 1 atau 2 |
| Mata_Pelajaran | Matematika, Bahasa Indonesia, Bahasa Inggris, IPA, IPS |
| Nilai_Tugas, Nilai_UTS, Nilai_UAS | Nilai 0–100 |
| Nilai_Akhir | 30% Tugas + 30% UTS + 40% UAS |
| Predikat | A (≥ 91), B (≥ 83), C (≥ 75), D (< 75) |
| Keterangan | Tuntas jika Nilai_Akhir ≥ 75 (KKM), selain itu Remedial |

### profil_belajar_siswa.csv
Satu baris = satu siswa. Fitur diambil dari Semester 1, target dari Semester 2.

| Kolom | Keterangan |
|---|---|
| NIS, Jenis_Kelamin, Kelas | Identitas siswa |
| Kehadiran_Persen | Persentase kehadiran |
| Jam_Belajar_Per_Minggu | Jam belajar mandiri di rumah |
| Ikut_Bimbel | Ya / Tidak |
| Akses_Internet_Rumah | Ya / Tidak |
| Rata_Tugas_Smt1, Rata_UTS_Smt1, Rata_Akhir_Smt1 | Rata-rata 5 mapel di Semester 1 |
| **Status_Smt2** | **Target**: Aman (230) atau Perlu Pendampingan (130), yaitu remedial di 2 mapel atau lebih pada Semester 2 |

Untuk latihan klaster, buang kolom `Status_Smt2` terlebih dahulu.

### umpan_balik_siswa.csv
Komentar siswa tentang pembelajaran, untuk latihan analisis sentimen.

| Kolom | Keterangan |
|---|---|
| ID_Umpan_Balik | Kode unik komentar |
| NIS | Siswa yang memberi komentar |
| Mata_Pelajaran | Mapel yang dikomentari |
| Komentar | Kalimat pendek berbahasa Indonesia |
| Bintang | Penilaian 1–5 |
| **Sentimen** | Positif (170), Negatif (70), Netral (60) |

---

## Contoh pertanyaan latihan

1. Menu apa yang paling laris, dan hari apa kedai paling ramai?
2. Mata pelajaran mana yang rata-rata nilainya di bawah KKM 75?
3. Apakah nilai siswa naik dari Semester 1 ke Semester 2?
4. Buat dasbor dengan filter Kelas dan Mata_Pelajaran.
5. Bisakah kita memprediksi siswa yang perlu pendampingan sebelum Semester 2 dimulai?
6. Kata apa yang sering muncul pada komentar bernada negatif?

## Lisensi

Bebas dipakai untuk keperluan pendidikan.

# Kamus Data Latihan Bertema Pendidikan

Data fiktif sebuah SMP (12 rombel, kelas VII–IX, 360 siswa). Nama siswa dibuat acak dan tidak merujuk orang sungguhan. Data ini menjadi alternatif latihan di samping data toko kopi, dengan alur yang sama: membaca data, memvisualisasikan, membuat dasbor, lalu memprediksi.

## 1. nilai_siswa.csv (3.600 baris, 13 kolom)
Satu baris = nilai satu siswa untuk satu mata pelajaran dalam satu semester (360 siswa × 5 mapel × 2 semester).

| Kolom | Isi |
|---|---|
| ID_Nilai | N00001–N03600 |
| NIS, Nama, Jenis_Kelamin (L/P), Kelas | Identitas siswa, kelas VII-1 sampai IX-4 |
| Semester | 1 atau 2 |
| Mata_Pelajaran | Matematika, Bahasa Indonesia, Bahasa Inggris, IPA, IPS |
| Nilai_Tugas, Nilai_UTS, Nilai_UAS | Bilangan bulat 0–100 |
| Nilai_Akhir | 30% Tugas + 30% UTS + 40% UAS, satu desimal |
| Predikat | A ≥ 91, B ≥ 83, C ≥ 75, D < 75 |
| Keterangan | Tuntas jika Nilai_Akhir ≥ 75 (KKM), selain itu Remedial |

Dipakai untuk P3 (Pandas: groupby, filter, rata-rata), P4 (grafik batang dan garis), dan P5 (dasbor Google Data Studio per kelas/mapel).

**Kunci angka:**
- Rata-rata Nilai_Akhir keseluruhan: 78,7 (Semester 1: 77,9, Semester 2: 79,6)
- Rata-rata per mapel: Bahasa Indonesia 82,0, IPS 80,9, Bahasa Inggris 79,0, IPA 77,1, Matematika 74,7 (satu-satunya di bawah KKM)
- Keterangan: Tuntas 2.552, Remedial 1.048
- Predikat: C 1.548, D 1.048, B 869, A 135
- Rata-rata per jenis kelamin: L 78,4, P 79,1
- Kelas tertinggi IX-1 (80,3), terendah VIII-4 (77,1)

## 2. profil_belajar_siswa.csv (360 baris, 11 kolom)
Satu baris = satu siswa. Fitur dari Semester 1, target dari Semester 2. Bentuknya setara dengan pelanggan_toko_kopi.csv.

| Kolom | Isi |
|---|---|
| NIS, Jenis_Kelamin, Kelas | Sama dengan nilai_siswa.csv (bisa digabung lewat NIS) |
| Kehadiran_Persen | 73–100 |
| Jam_Belajar_Per_Minggu | Jam belajar mandiri di rumah, 1–25 |
| Ikut_Bimbel, Akses_Internet_Rumah | Ya / Tidak |
| Rata_Tugas_Smt1, Rata_UTS_Smt1, Rata_Akhir_Smt1 | Rata-rata 5 mapel di Semester 1 |
| Status_Smt2 | **Target**: "Perlu Pendampingan" jika remedial ≥ 2 mapel di Semester 2, selain itu "Aman" |

Dipakai untuk P6–P7 (klasifikasi di Orange) dan P10 (klaster, dengan kolom Status_Smt2 dibuang).

**Kunci angka:**
- Status_Smt2: Aman 230, Perlu Pendampingan 130 (baseline tebak "Aman" = 63,9%)
- Akurasi validasi silang 5 lipatan (fitur selain NIS dan Kelas): Decision Tree kedalaman 4 sekitar 0,80, Logistic Regression sekitar 0,83. Angka di Orange bisa sedikit berbeda.
- Rata_Akhir_Smt1 siswa yang ikut bimbel 79,8, yang tidak 76,8

## 3. umpan_balik_siswa.csv (300 baris, 6 kolom)
Komentar siswa tentang pembelajaran, untuk P9 (analisis sentimen).

| Kolom | Isi |
|---|---|
| ID_Umpan_Balik | U0001–U0300 |
| NIS, Mata_Pelajaran | Siapa dan untuk mapel apa |
| Komentar | Kalimat pendek berbahasa Indonesia |
| Bintang | 1–5 |
| Sentimen | Positif 170, Negatif 70, Netral 60 |

## Ide latihan per pertemuan
- **P3:** Mapel mana yang rata-ratanya di bawah KKM? Berapa siswa remedial Matematika di semester 1?
- **P4:** Grafik batang rata-rata per mapel dengan garis KKM 75. Grafik garis rata-rata semester 1 ke semester 2.
- **P5:** Dasbor dengan filter Kelas dan Mata_Pelajaran, scorecard jumlah Tuntas/Remedial.
- **P6–P7:** Prediksi siswa yang perlu pendampingan sebelum semester 2 berjalan.
- **P9:** Hubungan Bintang dengan Sentimen; kata yang sering muncul di komentar negatif.
- **P10:** Kelompokkan siswa berdasarkan kehadiran, jam belajar, dan nilai.

Data dibuat ulang dengan `_pembuat_data.py` (seed 2026), jadi hasilnya selalu sama.

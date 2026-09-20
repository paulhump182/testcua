# Sistem Sensus Penduduk Indonesia 2024 + Otomasi Pengisian Formulir AI (CUA-S1-FORMS)

Aplikasi Web Sensus Penduduk Indonesia berbasis **PHP & MySQL/MariaDB (disertai phpMyAdmin)** yang terintegrasi dengan model kecerdasan buatan **CUA-S1-FORMS** (*Option-Attention Byte Transformer*) untuk otomasi pengisian formulir dari spreadsheet eksternal.


---

## 📄 Publikasi Karya Ilmiah & White Paper (PDF)

**Penulis / Author:** **Richie Octavian S.** (*Pemerhati AI dari Panita Community Gorontalo*)  
Karya ilmiah populer setebal **15 Halaman A4** yang menyajikan solusi otomasi formulir sensus menggunakan model AI CUA-S1 dengan bahasa yang mudah dipahami oleh orang awam (menggunakan analogi kognitif *System 1 vs System 2* dan dekonstruksi *Otak vs Tangan*), serta telah lulus audit mutu **Independent Peer Review** dengan predikat **APPROVED (Skor: 9.81 / 10.0)**.

Tersedia dalam dua versi bahasa resmi:
- 🇮🇩 **Edisi Bahasa Indonesia (PDF):** [**`Karya_Ilmiah_Model_AI_CUA_S1_Sensus.pdf`**](./Karya_Ilmiah_Model_AI_CUA_S1_Sensus.pdf) *(15 Halaman, 2.47 MB)*
- 🇬🇧 **English Edition (PDF):** [**`Scientific_Paper_CUA_S1_AI_Census_Form_Automation_EN.pdf`**](./Scientific_Paper_CUA_S1_AI_Census_Form_Automation_EN.pdf) *(13-15 Halaman, 2.44 MB)*
- 📝 **Naskah Sumber Markdown:** [`publikasi_ilmiah_cua/naskah_karya_ilmiah.md`](./publikasi_ilmiah_cua/naskah_karya_ilmiah.md)
- 🖼️ **Diagram Teknis & Infografis 300 DPI:**
  - [Diagram 1: Alur Sistem End-to-End Lapangan ke Intranet](./publikasi_ilmiah_cua/images/diagram_1_alur_sistem.png)
  - [Diagram 2: Arsitektur Neural Network Option-Attention Byte Transformer](./publikasi_ilmiah_cua/images/diagram_2_arsitektur_ai.png)
  - [Diagram 3: Infografis Evaluasi Model & Akselerasi Throughput 160x](./publikasi_ilmiah_cua/images/diagram_3_evaluasi_model.png)

---

## 📌 Latar Belakang Masalah & Solusi

### Masalah di Lapangan:
1. **Pengumpulan Data Lapangan:** Petugas di lapangan mengumpulkan data warga menggunakan formulir eksternal yang fleksibel (seperti Google Form, KoboToolbox, JotForm, atau spreadsheet ponsel).
2. **Keterbatasan Keamanan Sistem Utama:** Sistem sensus resmi dan database kependudukan utama berada di server internal/jaringan kantor yang aman dan terisolasi, sehingga **tidak boleh diakses dari internet publik** demi menjaga kerahasiaan NIK, Kartu Keluarga, dan privasi warga.
3. **Pekerjaan Berulang (*Data Re-entry*):** Akibatnya, petugas admin di kantor harus membuka hasil Google Form dan mengetikkan ulang (*manual re-entry*) ratusan hingga ribuan data warga satu per satu ke dalam aplikasi sensus internal. Proses ini melelahkan, memakan waktu berhari-hari, dan sangat rawan salah ketik (*human error*).

### Solusi dengan CUA-S1-FORMS:
Model AI **CUA-S1-FORMS** bertindak sebagai robot asisten kantor cerdas. Model AI ini membaca berkas hasil ekspor formulir eksternal (CSV), memahami pasangan label dan nilai secara mandiri, lalu mengisikan seluruh data ke aplikasi sensus internal serta menyimpannya ke database dalam hitungan detik.

---

## ✨ Fitur Utama

- **Formulir Interaktif 28 Kolom:** Mendukung seluruh kolom data kependudukan standar Indonesia (NIK, No KK, Umur, Hubungan Keluarga, Agama, Pekerjaan, Pendapatan, Wilayah Administratif 4 Tingkat, Fasilitas Perumahan, dll).
- **Dual-Mode Storage:** Menggunakan MySQL/MariaDB sebagai penyimpanan utama dengan sinkronisasi otomatis ke berkas CSV (dan *fallback* otomatis jika database mati).
- **phpMyAdmin 5.2.1 Terpasang:** Dilengkapi antarmuka GUI phpMyAdmin bawaan di `http://127.0.0.1:8000/phpmyadmin/` dengan konfigurasi *auto-login*.
- **Tabel Data Interaktif (`data.php`):** Dilengkapi pencarian langsung (*live search*), filter provinsi, pagination, dan modal pop-up untuk melihat 28 detail lengkap warga.
- **Dashboard Statistik Demografi (`statistik.php`):** Visualisasi grafik interaktif menggunakan Chart.js (piramida umur, jenis kelamin, tingkat pendidikan, dll).
- **Engine AI CUA-S1 Bawaan (`models/`):** Menyertakan model bobot Safetensors resmi (~2.8 MB, 706.048 parameter) sehingga dapat berjalan secara *offline*.
- **Batch Form Filler AI:** Skrip inferensi PyTorch berkecepatan tinggi (~16 data/detik di CPU) untuk memproses ratusan data sekaligus.

---

## 📁 Struktur Direktori

```text
├── README.md                                  # Dokumentasi utama proyek
├── Karya_Ilmiah_Model_AI_CUA_S1_Sensus.pdf    # Publikasi karya ilmiah Edisi Bahasa Indonesia (Richie Octavian S.)
├── Scientific_Paper_CUA_S1_AI_Census_Form_Automation_EN.pdf # Scientific Paper English Edition (Richie Octavian S.)
├── TUTORIAL_CUA_S1_FORMS.txt                  # Panduan lengkap ramah pemula (bahasa orang awam)
├── sensus_penduduk_indonesia_2024_dummy.csv   # Dataset 200 data sensus mentah standar 28 kolom
├── publikasi_ilmiah_cua/                      # Berkas sumber karya ilmiah & visual diagram
│   ├── naskah_karya_ilmiah.md                 # Naskah lengkap 8 bab Markdown
│   ├── build_pdf.py                           # Skrip kompilasi ReportLab layout jurnal A4
│   ├── generate_diagrams.py                   # Skrip render diagram 300 DPI Matplotlib
│   └── images/                                # Direktori berkas gambar PNG 300 DPI
│       ├── diagram_1_alur_sistem.png
│       ├── diagram_2_arsitektur_ai.png
│       └── diagram_3_evaluasi_model.png
└── aplikasi-sensus/                           # Folder aplikasi web & skrip AI
    ├── config.php                             # Konfigurasi koneksi MySQL PDO & CSV helper
    ├── index.php                              # Halaman formulir input sensus 28 kolom
    ├── proses_simpan.php                      # Handler POST penyimpanan ke MySQL & CSV
    ├── data.php                               # Tabel data kependudukan interaktif
    ├── statistik.php                          # Grafik & diagram analitik demografi
    ├── import.php                             # Fitur import spreadsheet via web
    ├── export.php                             # Fitur export data ke CSV
    ├── db_sensus.sql                          # Skema database MySQL & tabel penduduk
    ├── start.sh                               # Skrip aktivasi server PHP & MariaDB
    ├── reset_db_dan_csv.py                    # Skrip pengosongan cepat database
    ├── run_cua_model_test.py                  # Skrip uji coba model AI untuk 1 data warga
    ├── batch_cua_ai_filler.py                 # Skrip pengisian formulir massal ratusan baris
    ├── models/                                # Bobot model AI CUA-S1 (safetensors & json)
    ├── cua-repo/                              # Library resmi CUA-S1 dari GitHub
    ├── data/                                  # Salinan cadangan data mentah
    └── phpmyadmin/                            # phpMyAdmin 5.2.1 bawaan
```

---

## 🚀 Panduan Memulai (Quick Start)

### 1. Kebutuhan Sistem
- **PHP 8.0+** (dengan ekstensi `pdo_mysql`, `mbstring`)
- **MariaDB / MySQL 10.4+**
- **Python 3.10+**

### 2. Instalasi Dependensi Python
```bash
pip install torch transformers huggingface_hub safetensors requests
```

### 3. Persiapan Database
Impor skema database ke MySQL/MariaDB:
```bash
mysql -e "CREATE DATABASE IF NOT EXISTS db_sensus DEFAULT CHARACTER SET utf8mb4;"
mysql db_sensus < aplikasi-sensus/db_sensus.sql
```

### 4. Menjalankan Server Web
```bash
cd aplikasi-sensus
php -S 0.0.0.0:8000
```
- Akses Aplikasi: [http://127.0.0.1:8000/index.php](http://127.0.0.1:8000/index.php)
- Akses Data: [http://127.0.0.1:8000/data.php](http://127.0.0.1:8000/data.php)
- Akses phpMyAdmin: [http://127.0.0.1:8000/phpmyadmin/](http://127.0.0.1:8000/phpmyadmin/)

---

## 🤖 Menjalankan Model AI CUA-S1

### Uji Coba 1 Data Warga (Single Record Test)
```bash
python3 aplikasi-sensus/run_cua_model_test.py
```
*Output menampilkan kalkulasi neural network dan persentase keyakinan tindakan form-filling:*
```text
================ HASIL PREDIKSI MODEL AI CUA-S1 ================
 [EDIT  ] Policy #             -> FILL : '3273010106240003' (100.0%)
 [EDIT  ] Full name            -> FILL : 'Farhan Alamsyah, M.T.' ( 86.3%)
 [EDIT  ] Date of birth        -> FILL : '1996-05-19' (100.0%)
 [EDIT  ] City                 -> FILL : 'Kota Bandung' ( 99.9%)
 [EDIT  ] Street address       -> FILL : 'Jl. Sangkuriang Barat No. 12' (100.0%)
 [EDIT  ] Insurance provider   -> FILL : 'BPJS Non-PBI / Mandiri' ( 99.4%)
 [BUTTON] Submit               -> CLICK: Eksekusi Submit (100.0%)
✓ BERHASIL! Data telah tersimpan di MySQL (db_sensus) dan berkas CSV.
```

### Pengisian Massal Ratusan Baris (Batch Form Filling)
```bash
# Memproses 10 data pertama:
python3 aplikasi-sensus/batch_cua_ai_filler.py --limit 10

# Memproses SELURUH 200 data warga dari spreadsheet:
python3 aplikasi-sensus/batch_cua_ai_filler.py --limit 0
```

---

## 📚 Panduan Lengkap untuk Pemula
Untuk penjelasan langkah-demi-langkah dalam bahasa Indonesia yang santai dan ramah bagi orang awam, silakan baca berkas:
👉 **[`TUTORIAL_CUA_S1_FORMS.txt`](./TUTORIAL_CUA_S1_FORMS.txt)**

---

## 🔗 Referensi & Kredit
1. **Model Hugging Face:** [cua-ai/cua-s1-forms](https://huggingface.co/cua-ai/cua-s1-forms)
2. **Repositori CUA Resmi:** [trycua/cua](https://github.com/trycua/cua)
3. **Video Referensi:** [YouTube - CUA S1 Forms Tutorial](https://www.youtube.com/watch?v=Rzgd-y3mCPs)

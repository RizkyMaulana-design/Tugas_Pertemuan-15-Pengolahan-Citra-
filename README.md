```python
# Generate the fully translated and detailed professional README.md in Indonesian
readme_content = """# 🚶‍♂️ Deteksi Pejalan Kaki menggunakan HOG + Linear SVM (OpenCV-Python)

Implementasi Python yang komprehensif dan teroptimasi untuk mendeteksi pejalan kaki, baik pada citra statis (gambar) maupun *streaming* video secara *real-time*. Proyek ini memanfaatkan algoritma ekstraksi fitur **Histogram of Oriented Gradients (HOG)** yang dikombinasikan dengan pengklasifikasi **Linear Support Vector Machine (SVM)**.

Repositori ini disusun sebagai pemenuhan Tugas Mata Kuliah Pengolahan Citra Digital.

---

## 👤 Profil Akademik
* **Nama:** Rizky Maulana
* **NIM:** 312410430
* **Kelas:** I241C
* **Dosen Pengampu:** ```python
# Generate the fully translated and detailed professional README.md in Indonesian
readme_content = """# 🚶‍♂️ Deteksi Pejalan Kaki menggunakan HOG + Linear SVM (OpenCV-Python)

Implementasi Python yang komprehensif dan teroptimasi untuk mendeteksi pejalan kaki, baik pada citra statis (gambar) maupun *streaming* video secara *real-time*. Proyek ini memanfaatkan algoritma ekstraksi fitur **Histogram of Oriented Gradients (HOG)** yang dikombinasikan dengan pengklasifikasi **Linear Support Vector Machine (SVM)**.

Repositori ini disusun sebagai pemenuhan Tugas Mata Kuliah Pengolahan Citra Digital.

---

## 👤 Profil Akademik
* **Nama:** Rizky Maulana
* **NIM:** 312410430
* **Kelas:** I241C
* **Dosen Pengampu:** Donny Maulana, S.Kom., M.M.S.I.
* **Mata Kuliah:** Pengolahan Citra Digital

---

## 🚀 Fitur Utama
* **Deteksi Citra Statis (*Static Image Detection*):** Mengekstrak orientasi gradien untuk melacak siluet manusia dan menandainya dengan *bounding box* yang presisi.
* **Deteksi Video Real-Time (*Dynamic Video Tracking*):** Memproses aliran video dari *frame* ke *frame* untuk melacak pergerakan beberapa pejalan kaki secara bersamaan.
* **Presisi Rasio Aspek (*Aspect-Ratio Awareness*):** Memanfaatkan pustaka `imutils` untuk mengubah ukuran citra secara proporsional, memastikan koordinat *bounding box* tetap akurat tanpa mendistorsi gambar asli.

---

## 🛠️ Kebutuhan Sistem & Teknologi
Proyek ini dibangun menggunakan bahasa pemrograman Python dengan pustaka *Computer Vision* berikut:
* **Python 3.x**
* **OpenCV (`opencv-python`):** Pustaka utama untuk pemrosesan citra digital dan pemanfaatan model *pre-trained* pendeteksi HOG (HOG Descriptor).
* **Imutils:** Pustaka pendukung untuk efisiensi fungsi manipulasi citra, khususnya proses *resizing*.

---

## 📂 Struktur Direktori

```

```text
README.md (Indonesian & Detailed) successfully created.

```text
Tugas_Citra_Rizky_312410430/
├── deteksi_gambar.py   # Skrip utama pendeteksi pejalan kaki pada gambar
├── deteksi_video.py    # Skrip utama pendeteksi pejalan kaki pada video
├── img.jpg             # Aset citra masukan untuk pengujian
├── vid.mp4             # Aset video masukan untuk pengujian
└── README.md           # Dokumentasi teknis proyek

```

---

## 🔧 Panduan Instalasi

1. **Kloning Repositori**
Gunakan perintah berikut untuk mengunduh repositori ke lingkungan kerja lokal Anda:
```bash
git clone [https://github.com/RizkyMaulana-design/Pedestrian-Detection-HOG.git](https://github.com/RizkyMaulana-design/Pedestrian-Detection-HOG.git)
cd Tugas_Citra_Rizky_312410430

```


2. **Instalasi Dependensi**
Pastikan Anda menginstal pustaka yang diperlukan melalui terminal/command prompt:
```bash
pip install opencv-python imutils

```


3. **Persiapan Aset Media**
* Letakkan gambar target di dalam folder direktori ini dan pastikan bernama `img.jpg`.
* Letakkan video target di dalam folder direktori ini dan pastikan bernama `vid.mp4`.



---

## 💻 Instruksi Eksekusi Program

### 1. Eksekusi Deteksi Gambar

Untuk mendeteksi pejalan kaki pada gambar statis, jalankan:

```bash
python deteksi_gambar.py

```

*Tekan sembarang tombol pada *keyboard* (atau klik tombol *close*) untuk menutup jendela *output* gambar.*

### 2. Eksekusi Deteksi Video

Untuk mendeteksi dan melacak pejalan kaki secara dinamis pada video, jalankan:

```bash
python deteksi_video.py

```

*Tekan tombol **'q'** pada *keyboard* Anda untuk menghentikan proses *streaming* dan menutup jendela video.*

---

## 🔬 Tinjauan Metodologi Terdalam (Berdasarkan Dalal & Triggs, 2005)

Arsitektur aplikasi ini dibangun berdasarkan prinsip dasar dari riset fundamental *Computer Vision* oleh Navneet Dalal dan Bill Triggs pada paper **"Histograms of Oriented Gradients for Human Detection"** (CVPR 2005). Berikut adalah rincian teknis dari algoritma pendeteksi ini:

1. **Komputasi Gradien Cita (Tanpa *Smoothing*):** Langkah pertama adalah menghitung turunan spasial gambar (gradien). Algoritma ini menggunakan filter turunan 1-D sederhana, yaitu matriks `[-1, 0, 1]`. Riset membuktikan bahwa penerapan *smoothing* (seperti filter Gaussian) pada tahap ini justru menurunkan performa. Gradien harus dihitung pada piksel tertajamnya agar struktur tepi (*edges*) tubuh manusia dapat tertangkap secara detail.
2. ***Spatial* & *Orientation Binning* (Penempatan Bin):** Setiap piksel dalam gambar menghitung "suara" (*vote*) untuk orientasi tepi berdasarkan magnitudo gradiennya. Gambar dibagi menjadi sel-sel kecil (misalnya, $8\times8$ piksel). Orientasi tersebut kemudian didistribusikan ke dalam **9 *bin* orientasi** yang membentang dari $0^\circ$ hingga $180^\circ$ (mengabaikan nilai minus/gradien "tidak bertanda").
3. **Normalisasi Blok Terpusat (*Block Normalization - L2-Hys*):** Pencahayaan di dunia nyata sangat bervariasi (bayangan, transisi gelap-terang). Untuk mengatasinya, sel-sel tadi dikelompokkan ke dalam "blok" yang saling tumpang tindih (*overlapping blocks*). Energi lokal di dalam setiap blok dihitung untuk menormalisasi nilai kontras pada sel tersebut. Sistem ini menggunakan teknik kliping *L2-norm* (*L2-Hys*), yang krusial untuk menjadikan algoritma kebal terhadap gangguan perubahan cahaya lingkungan.
4. **Klasifikasi via Linear SVM:** Seluruh vektor HOG dari berbagai blok digabungkan menjadi satu deksriptor fitur komprehensif. Vektor ini kemudian dievaluasi menggunakan *Support Vector Machine (SVM)* linier yang sebelumnya telah dilatih menggunakan ribuan data citra manusia (seperti set data MIT atau INRIA). Menariknya, sistem pengklasifikasi ini tidak berfokus pada area *internal* objek, melainkan menyoroti kontur siluet pejalan kaki—terutama pada kontras area kepala, bahu, dan kaki terhadap latar belakangnya.

---


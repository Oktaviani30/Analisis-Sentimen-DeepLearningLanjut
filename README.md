# Analisis-Sentimen-DeepLearningLanjut
Tugas Analisis Sentimen menggunakan model Transformer (BERT). Proyek ini mencakup fine-tuning pada 300 data berlabel dan pelabelan otomatis pada 400 data pengujian.
Tugas Kelompok: Analisis Sentimen Menggunakan Model Transformer

Repository ini dibuat untuk memenuhi tugas mata kuliah 

$$Deep Learning Lanjut$$

, yang berfokus pada implementasi arsitektur Transformer untuk klasifikasi teks otomatis.

👥 Anggota Kelompok

Nike Oktaviani NIM_41236767

Putri Regina NIM_41236774


📝 Deskripsi Tugas

Tugas ini melibatkan proses fine-tuning model Transformer (IndoBERT) untuk melakukan pelabelan sentimen pada data yang tidak berlabel.

Dataset yang Digunakan:

Data Pelatihan (train.csv): 300 kalimat bahasa Indonesia (100 Positif, 100 Negatif, 100 Netral).

Data Pengujian (test.csv): 400 kalimat tanpa label awal.

Hasil Prediksi (hasil_pelabelan_kelompok.csv): Label otomatis yang dihasilkan oleh model setelah proses pelatihan.

🚀 Implementasi Model

Kami menggunakan model IndoBERT (indobenchmark/indobert-base-p1) dari Hugging Face. Proses pengerjaan dilakukan di Google Colab dengan memanfaatkan akselerasi GPU T4 untuk efisiensi waktu pelatihan.

Alur Kerja:

Persiapan: Menghubungkan Google Drive untuk penyimpanan dataset.

Preprocessing: Tokenisasi teks menggunakan tokenizer IndoBERT.

Fine-tuning: Melatih model selama 3 epoch pada dataset 300 baris.

Inference: Menggunakan model hasil pelatihan untuk memprediksi sentimen pada 400 data uji.

📊 Hasil

Model Grafik dibawah berhasil mengklasifikasikan 400 data pengujian ke dalam tiga kategori (Positif, Negatif, Netral) berdasarkan pola makna yang dipelajari dari data pelatihan.
 import matplotlib.pyplot as plt
import seaborn as sns

# 1. Hitung jumlah tiap sentimen dari hasil tebakan
counts = df_test['sentiment_prediction'].value_counts()

# 2. Buat visualisasi
plt.figure(figsize=(8, 6))
sns.barplot(x=counts.index, y=counts.values, palette='viridis')

# 3. Tambah judul dan keterangan
plt.title('Distribusi Hasil Prediksi Sentimen (400 Data Test)', fontsize=14)
plt.xlabel('Kategori Sentimen', fontsize=12)
plt.ylabel('Jumlah Kalimat', fontsize=12)

# Tampilkan angka di atas batang
for i, v in enumerate(counts.values):
    plt.text(i, v + 5, str(v), ha='center', fontweight='bold')

plt.show()

  ## 🛠️ Teknologi yang Digunakan
- Python
- Google Colab (GPU T4)
- Hugging Face Transformers Library
- PyTorch
- Pandas & Matplotlib

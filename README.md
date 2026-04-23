# 🔍 Sentiment Analysis Ulasan Aplikasi DANA
 
Proyek ini membangun sistem klasifikasi sentimen terhadap ulasan pengguna aplikasi **DANA** dari Google Play Store, menggunakan berbagai kombinasi model machine learning dan teknik ekstraksi fitur.
 
---
 
## 📌 Deskripsi Proyek
 
Ulasan pengguna di Play Store menjadi sumber informasi berharga untuk memahami kepuasan pelanggan. Proyek ini mengklasifikasikan ulasan ke dalam tiga kelas sentimen:
 
| Label | Keterangan | Skor Rating |
|-------|-----------|-------------|
| 🔴 Negative | Ulasan negatif / keluhan | ⭐ 1–2 |
| 🟡 Neutral | Ulasan netral | ⭐ 3 |
| 🟢 Positive | Ulasan positif / pujian | ⭐ 4–5 |
 
---
 
## 📁 Struktur Proyek
 
```
📦 sentiment-analysis-dana/
├── 📂 notebook/
│   ├── 📓 01_data_scraping.ipynb                    # Scraping ulasan dari Google Play Store
│   ├── 📓 02_data_labeling_and_preprocessing.ipynb  # Pelabelan & preprocessing teks
│   ├── 📓 03_data_modeling.ipynb                    # Pelatihan & perbandingan model
│   └── 📓 04_inference.ipynb                        # Prediksi teks baru
├── 📂 data/
│   ├── 📄 dana_reviews.csv                          # Dataset mentah hasil scraping
│   └── 📄 dana_preprocessing.csv                   # Dataset setelah preprocessing
├── 📂 model/
│   ├── 🤖 model_lstm_bow.h5                         # Model terbaik (LSTM + BoW)
│   └── 🗜️ bow_vectorizer.pkl                        # Vectorizer BoW yang disimpan
└── 📄 requirements.txt                              # Daftar dependensi
```
 
---
 
## 🔄 Alur Kerja
 
```
Google Play Store
      │
      ▼
01. Data Scraping          → 15.000 ulasan aplikasi DANA
      │
      ▼
02. Labeling & Preprocessing
   ├── Pelabelan berdasarkan skor rating
   ├── Case folding
   ├── Pembersihan karakter khusus
   ├── Normalisasi kata slang (indoNLP)
   ├── Tokenisasi
   └── Stemming (Sastrawi)
      │
      ▼
03. Modeling (9 kombinasi)
   ├── Feature Extraction: BoW | TF-IDF | Word2Vec
   └── Model: SVM | RNN | LSTM  (+Optuna hyperparameter tuning)
      │
      ▼
04. Inference              → Prediksi teks baru + confidence score
```
 
---
 
## 📊 Perbandingan Performa Model
 
| Feature Extraction | SVM | RNN | LSTM |
|---|---|---|---|
| **BoW** | 85.81% | 86.61% | **86.72% ✅** |
| **TF-IDF** | 86.30% | 86.09% | 86.37% |
| **Word2Vec** | **85.56%** | 85.11% | 85.04% |
 
> ✅ **Model terbaik: LSTM + BoW** dengan akurasi **86.72%**
 
---
 
## 🛠️ Tech Stack
 
| Kategori | Library | Versi |
|---|---|---|
| Scraping | `google-play-scraper` | 1.2.7 |
| Data Processing | `pandas`, `numpy` | 3.0.2, 2.4.4 |
| Visualisasi | `matplotlib` | 3.10.8 |
| NLP (Bahasa Indonesia) | `indoNLP`, `Sastrawi`, `NLTK` | 0.3.4, 1.0.1, 3.9.4 |
| Machine Learning | `scikit-learn` (SVM) | 1.8.0 |
| Deep Learning | `TensorFlow / Keras` (RNN, LSTM) | 2.21.0 |
| Word Embedding | `gensim` (Word2Vec) | 4.4.0 |
| Hyperparameter Tuning | `optuna` | 4.8.0 |
| Model Saving | `joblib` | 1.5.3 |
 
---

## 🧪 Contoh Hasil Prediksi
 
| Teks | Prediksi | Confidence |
|---|---|---|
| *"saldo tidak dikembalikan ke nomor baru padahal sudah ikuti prosedur"* | 🔴 Negative | 0.8077 |
 
---
 
## 📝 Catatan
 
- Scraping dilakukan pada periode tertentu; hasil dapat berbeda jika dijalankan ulang
- Preprocessing menggunakan kamus slang bahasa Indonesia dari `indoNLP`
- Hyperparameter tuning menggunakan **Optuna TPE Sampler** dengan 15 trials per model
- Model disimpan dalam format `.h5` (Keras) dan `.pkl` (joblib)
---

## 🏫 Program

Proyek ini merupakan hasil dari **DBS Coding Camp Learning Path AI Engineer 2026**

---

## 👤 Author
 
**[Aliyah Nadhratunnaim]**  
📧 aliyah180606@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/aliyahnadhratunnaim) | [GitHub](https://github.com/aliyahnadh)














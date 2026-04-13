## Analisis Faktor yang Mempengaruhi Keberhasilan Aplikasi pada Google Play Store
**Dataset** : [source](https://www.rakamin.com/virtual-internship-experience/data-scientist-home-credit-indonesia) <br>
**Python Code** : [view](https://github.com/faizns/HCI-vix-project/blob/main/HCI_VIX.ipynb)<br>

<br>

**Table of Contents**
- [Business Understanding](https://github.com/faizns/HCI-vix-project/blob/main/README.md#-business-understanding)
- [Workflow](https://github.com/faizns/HCI-vix-project/blob/main/README.md#-workflow)
- [Insight](https://github.com/faizns/HCI-vix-project/blob/main/README.md#-insight)
- [Modeling and Evaluation](https://github.com/faizns/HCI-vix-project/blob/main/README.md#-modeling-and-evaluation)
- [Model Simulation using Streamlit](https://github.com/faizns/HCI-vix-project/blob/main/README.md#-model-simulation-using-streamlit)
<br>

## 📂 Business Understanding

### **Problem Statement**

Saat ini, aplikasi di Google Play Store jumlahnya sangat banyak dan terus bertambah. Hal ini membuat persaingan antar aplikasi menjadi semakin tinggi.

Developer sering kesulitan memahami faktor apa saja yang membuat sebuah aplikasi bisa sukses, seperti jumlah download, rating, harga, dan kategori aplikasi.

Jika tidak dianalisis dengan baik, aplikasi yang dibuat bisa kurang diminati oleh pengguna dan sulit bersaing di pasaran.

### **Goals**

- Mengetahui faktor yang mempengaruhi keberhasilan aplikasi
- Membantu developer memahami preferensi pengguna
- Mendukung pengambilan keputusan dalam pengembangan aplikasi

### **Objectives**

- Menganalisis hubungan antara rating, size, price, dan kategori dengan jumlah install
- Mengidentifikasi pola aplikasi yang sukses dan kurang sukses
- (Opsional) Membuat model sederhana untuk memprediksi keberhasilan aplikasi

## 📂 Workflow

### 1. Pengumpulan Data

Dataset yang digunakan merupakan dataset Google Play Store yang berisi informasi mengenai aplikasi, seperti kategori, rating, jumlah installs, ukuran aplikasi, harga, dan lain-lain.

### 2. Data Cleaning & Preprocessing

Pada tahap ini dilakukan pembersihan dan persiapan data agar siap dianalisis, meliputi:

- Menghapus data duplikat
- Menangani missing values (nilai kosong)
- Mengubah format data:
    - Kolom *Installs* diubah menjadi numerik
    - Kolom *Price* diubah menjadi numerik
    - Kolom *Size* diseragamkan ke dalam satuan yang konsisten
- Menghapus data yang tidak relevan atau outlier jika diperlukan

### 3. Exploratory Data Analysis (EDA)

Tahap ini bertujuan untuk memahami karakteristik data, dengan cara:

- Melihat distribusi data (rating, installs, dll)
- Mengidentifikasi pola awal
- Menemukan hubungan antar variabel

### 4. Visualisasi Data

Data divisualisasikan agar lebih mudah dipahami, menggunakan:

- Bar chart → untuk melihat perbandingan antar kategori
- Histogram → untuk distribusi data
- Scatter plot → untuk melihat hubungan antar variabel

### 5. Penarikan Insight

Berdasarkan hasil analisis dan visualisasi, dilakukan penarikan insight seperti:

- Faktor yang mempengaruhi jumlah installs
- Karakteristik aplikasi yang sukses
- Pola perilaku pengguna terhadap aplikasi

### 6. Modeling

Jika dilakukan, tahap ini bertujuan untuk membangun model sederhana, seperti:

- Mengklasifikasikan aplikasi sukses atau tidak berdasarkan jumlah installs
- Menggunakan algoritma seperti Logistic Regression atau Random Forest

### 7. Evaluasi

Model yang dibuat dievaluasi menggunakan metrik seperti:

- Accuracy
- Precision / Recall
- AUC

Hasil evaluasi digunakan untuk menilai performa model dalam memprediksi keberhasilan aplikasi

## 📂 Insight

### Distribusi Rating Aplikasi
<img width="560" height="435" alt="image" src="https://github.com/user-attachments/assets/9d5f4dd8-7768-4d0e-b240-a7aa502654de" />

### Insight:

Sebagian besar aplikasi memiliki rating di kisaran **4.0 – 4.5**, yang menunjukkan bahwa mayoritas aplikasi di Google Play Store memiliki kualitas yang cukup baik menurut pengguna.

Namun, terdapat sedikit aplikasi dengan rating rendah (< 3), yang mengindikasikan adanya aplikasi dengan performa atau pengalaman pengguna yang kurang optimal.

## Kategori Aplikasi Terpopuler
<img width="560" height="570" alt="image" src="https://github.com/user-attachments/assets/940124e7-562b-4119-bd21-9c67ec934161" />

### Insight:

Kategori **Family** dan **Game** merupakan kategori dengan jumlah aplikasi terbanyak di Google Play Store.

Hal ini menunjukkan bahwa:

- Kedua kategori tersebut memiliki **permintaan tinggi**
- Namun juga memiliki **tingkat persaingan yang sangat tinggi**

## Hubungan Rating vs Installs
<img width="567" height="455" alt="image" src="https://github.com/user-attachments/assets/6b4dcbbc-c3b7-4c39-92c5-ab8867440f7c" />

### Insight:

Tidak terdapat hubungan linear yang kuat antara rating dan jumlah installs.

Beberapa aplikasi dengan rating tinggi tidak selalu memiliki jumlah install yang besar, sementara ada aplikasi dengan rating sedang yang memiliki jumlah install sangat tinggi.

Artinya:

> Keberhasilan aplikasi tidak hanya ditentukan oleh rating, tetapi juga dipengaruhi oleh faktor lain seperti branding, marketing, dan kebutuhan pasar.
> 

## Free vs Paid Apps

- Free: **17.7 juta (rata-rata installs)**
- Paid: **113 ribu**

### Insight:

Aplikasi gratis memiliki jumlah installs yang jauh lebih tinggi dibandingkan aplikasi berbayar.
Hal ini menunjukkan bahwa:

- Model bisnis **freemium lebih dominan**
- Pengguna cenderung memilih aplikasi gratis dibandingkan berbayar

> Secara keseluruhan, keberhasilan aplikasi tidak hanya ditentukan oleh satu faktor, melainkan kombinasi dari berbagai aspek seperti kategori, strategi harga, dan kebutuhan pengguna.
> 

## 📂 Modeling and Evaluation

### Modeling

Model yang digunakan adalah **Logistic Regression** untuk mengklasifikasikan apakah sebuah aplikasi termasuk sukses atau tidak berdasarkan jumlah installs.

Target didefinisikan sebagai:

- **1 (Success)**: aplikasi dengan jumlah installs > 100.000
- **0 (Tidak)**: aplikasi dengan jumlah installs ≤ 100.000

Distribusi data target relatif seimbang:

- Success: 4566
- Tidak: 4320

### Evaluasi Model

**Accuracy**

Model menghasilkan akurasi sebesar **64%**, yang menunjukkan bahwa model mampu mengklasifikasikan data dengan cukup baik, meskipun masih terdapat ruang untuk peningkatan.

**Confusion Matrix**

```
[[498 377]
 [256 647]]
```

**Insight:**

- Model cukup baik dalam mengidentifikasi aplikasi **sukses (647 benar)**
- Namun masih terdapat kesalahan klasifikasi, terutama pada:
    - False Positive (377)
    - False Negative (256)

**Precision & Recall**

- Precision (Success): **0.63**
- Recall (Success): **0.72**

**Insight:**

Model memiliki **recall yang cukup tinggi** untuk kelas “sukses”, yang berarti model cukup baik dalam mendeteksi aplikasi yang benar-benar sukses. Namun, precision yang lebih rendah menunjukkan bahwa masih terdapat prediksi “sukses” yang sebenarnya tidak sukses.

**AUC Score**

Nilai AUC sebesar **0.68** menunjukkan bahwa model memiliki kemampuan yang cukup baik dalam membedakan antara aplikasi yang sukses dan tidak.
Model mampu menangkap pola dasar dari data, namun performanya masih terbatas. Hal ini mengindikasikan bahwa keberhasilan aplikasi tidak hanya dipengaruhi oleh fitur sederhana seperti rating, size, dan price, tetapi juga faktor lain seperti strategi pemasaran, user experience, dan brand awareness.

### Kesimpulan

- Model Logistic Regression memberikan performa yang **cukup baik (moderate performance)**
- Model lebih fokus menangkap aplikasi sukses (recall tinggi)
- Masih terdapat ruang peningkatan dengan:
    - penambahan fitur
    - penggunaan model yang lebih kompleks

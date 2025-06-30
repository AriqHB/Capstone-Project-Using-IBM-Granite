# 📧 Capstone Project: Email Classification & Summarization using IBM Granite

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1iZ63pK5JgcquYXSeRkJ7ahLcIYD5Ih3y?usp=sharing)

## 🔍 Project Overview

- **Tujuan:** Membangun pipeline AI untuk klasifikasi otomatis dan ringkasan email bisnis.
- **Latar belakang:** Ribuan email bisnis memakan waktu analisis manual; AI dapat mempercepat, menstrukturkan, dan memberikan insight real‑time.
- **Permasalahan:**  
  1. Mengkategorikan email ke salah satu dari 5 domain bisnis.  
  2. Meringkas setiap email ke 1–3 kalimat yang fokus dan relevan.  

## 📂 Raw Dataset

Dataset publik yang digunakan:
- **Nama:** Enron Email Dataset  
- **Link:** [Kaggle - Enron Email Dataset](https://www.kaggle.com/datasets/wcukierski/enron-email-dataset)  
- **Jumlah email yang dianalisis:** 1000 email

## 🧠 AI Support Explanation

Model yang digunakan:
- **Model LLM:** `ibm-granite/granite-3.3-8b-instruct` (via [Replicate](https://replicate.com))
- **Tugas AI:**
  - **Email Classification**: Mengklasifikasikan isi email ke dalam 5 kategori spesifik.
  - **Summarization**: Meringkas isi utama email dalam 1–3 kalimat ringkas dan padat informasi.

> AI digunakan sebagai *digital analyst* untuk membaca, memahami, dan menyusun kembali email secara efisien dan akurat.

## 🧪 Analysis Process

1. **Pengambilan Data**  
   Mengambil 1000 email secara acak dari dataset Enron.

2. **Ekstraksi**  
   Parsing konten email mentah untuk mengambil: `Date`, `From`, `To`, `Subject`, dan `Body`.

3. **Klasifikasi & Ringkasan (LLM)**  
   Mengirim konten email ke model dengan prompt terstruktur yang memastikan output sesuai dan terstandarisasi.

4. **Exploratory Data Analysis (EDA)**  
   Menghitung distribusi kategori, mengonversi ke persentase, dan menyusun insight administratif.

## 📈 Analytical Result

Hasil klasifikasi dari 1000 email:

| Kategori                                    | Jumlah | Persentase |
|---------------------------------------------|--------|------------|
| Business Operations & Logistics             | 455    | 45.5%      |
| Financial & Legal                           | 206    | 20.6%      |
| Internal Company & HR                       | 153    | 15.3%      |
| Personal & Informal                         | 99     | 9.9%       |
| External Communications & Public Relations | 87     | 8.7%       |

![Distribusi Kategori Email](https://github.com/AriqHB/Capstone-Project-Using-IBM-Granite/blob/88ba8c8c88948fa021233173ade815757e14d17a/Distribusi%20Kategori%20Email.png)

## 💡 Insight & Findings

- **Kategori dominan:** Business Operations & Logistics (45.5%) menunjukkan frekuensi tinggi dalam komunikasi operasional.
- **Tingginya volume keuangan & hukum:** Menunjukkan kebutuhan kontrol dan pelaporan yang konstan.
- **Konten informal tetap muncul:** Sekitar 10% email menunjukkan percakapan non-formal antar pegawai.

## ✅ Recommendations

- **Otomasi klasifikasi email masuk** untuk mempercepat workflow dan mengurangi kelelahan administratif.
- **Audit komunikasi informal** untuk menjaga profesionalisme dan efisiensi email.
- **Integrasi dengan sistem manajemen proyek/logistik** berdasarkan email operasional yang dominan.
- **Pemantauan kepatuhan regulasi** melalui klasifikasi konten keuangan & legal secara otomatis.

---

## 📜 Prompt & Model Settings

### 🔄 Final Prompt Structure

```

You are an AI email classifier. Classify the email into exactly one of the following categories with no deviations:

* Business Operations & Logistics (e.g., project updates, equipment issues)
* Internal Company & HR (e.g., staff memos, internal meetings)
* Financial & Legal (e.g., contracts, regulatory, accounting)
* External Communications & Public Relations (e.g., media, partners, external clients)
* Personal & Informal (e.g., social chats, jokes, non-work content)

Respond strictly in this format:
Category: <selected category>
Summary: \<no more than 3 sentences summary of key content only>

Email:
From: ...
Subject: ...
Body: ...

```

### ⚙️ Model Settings (via Replicate)

| Parameter             | Value        | Fungsi                                                                 |
|----------------------|--------------|------------------------------------------------------------------------|
| `max_new_tokens`     | 1000         | Cakupan cukup untuk label & ringkasan                                 |
| `temperature`        | 0.2          | Meningkatkan konsistensi dan deterministik output                     |
| `top_p`              | 0.9          | Mengizinkan variasi jawaban tetapi tetap terkontrol                   |
| `top_k`              | 40           | Memfokuskan output pada top-k token terpenting                        |
| `repetition_penalty`| 1.2          | Mengurangi pengulangan frasa                                           |

> Prompt ini dioptimalkan agar **terstruktur, bebas halusinasi**, dan mudah diproses secara downstream (untuk analisis lanjutan atau sistem otomatisasi lainnya).

---

## ✨ Credits

- Dataset oleh [Kaggle - Enron Email Dataset](https://www.kaggle.com/datasets/wcukierski/enron-email-dataset)
- LLM Inference oleh [Replicate](https://replicate.com)
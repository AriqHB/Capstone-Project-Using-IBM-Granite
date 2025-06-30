# 📧 Capstone Project: Email Classification & Summarization using IBM Granite

## 🔍 Project Overview

Proyek ini bertujuan untuk mengembangkan sistem klasifikasi dan peringkasan otomatis terhadap email menggunakan Large Language Model (LLM) IBM Granite. Dengan meningkatnya volume komunikasi bisnis digital, otomatisasi analisis email sangat penting untuk meningkatkan efisiensi, menemukan pola komunikasi penting, serta menyederhanakan proses pengambilan keputusan.

Melalui proyek ini, dilakukan proses analisis email internal perusahaan untuk mengkategorikan isi pesan ke dalam 5 kategori utama serta merangkum informasi pentingnya dalam bentuk ringkas dan relevan.

> **Tujuan:** Membangun sistem berbasis AI yang mampu mengklasifikasikan email secara akurat dan menghasilkan ringkasan berkualitas untuk mendukung insight bisnis.

## 📂 Raw Dataset

Dataset publik yang digunakan:
- **Nama:** Enron Email Dataset  
- **Link:** [Kaggle - Enron Email Dataset](https://www.kaggle.com/datasets/wcukierski/enron-email-dataset)  
- **Jumlah email yang dianalisis:** 1000 sampel (dapat diperluas)

## 🧠 AI Support Explanation

Model yang digunakan:
- **Model LLM:** `ibm-granite/granite-3.3-8b-instruct` (via [Replicate](https://replicate.com))
- **Tugas AI:**
  - **Email Classification**: Mengklasifikasikan isi email ke dalam 5 kategori spesifik.
  - **Summarization**: Meringkas isi utama email dalam 1–3 kalimat ringkas.

> AI berperan sebagai *knowledge worker assistant* dalam membaca, memahami, dan menyusun kembali email layaknya seorang analis profesional.

## 🧪 Analysis Process

1. **Pengambilan Data**  
   Mengambil 100 email secara acak dari dataset Enron.

2. **Ekstraksi**  
   Parsing data email mentah untuk mengambil komponen: `Date`, `From`, `To`, `Subject`, dan `Body`.

3. **Klasifikasi & Ringkasan (AI-Inference)**  
   Mengirim email ke model LLM untuk klasifikasi dan peringkasan. Digunakan *prompt engineering* agar model memberikan jawaban terstruktur dan relevan.

4. **Exploratory Data Analysis (EDA)**  
   Menganalisis hasil klasifikasi & ringkasan email untuk melihat distribusi kategori, pola dominan, serta insight menarik.

## 📈 Analytical Result

Hasil klasifikasi dari 100 email:

- **Business Operations & Logistics**: 28%
- **Financial & Legal**: 24%
- **Internal Company & HR**: 18%
- **External Communications & PR**: 15%
- **Personal & Informal**: 15%

Terdapat distribusi yang seimbang dengan dominasi pada email operasional dan keuangan.

## 💡 Insight & Findings

- **Kategori dominan**: Email terkait operasional dan keuangan merupakan komunikasi utama di lingkungan korporat.
- **Pola korespondensi internal**: Banyak diskusi internal mengenai kontrak, proyek, hingga logistik teknis.
- **Personal content**: Meski minor, masih ditemukan komunikasi informal yang menjadi sinyal budaya organisasi terbuka.

## ✅ Recommendations

- **Automasi filter email masuk berdasarkan kategori** untuk mempercepat alur kerja dan mengurangi beban manual.
- **Penerapan klasifikasi serupa pada sistem helpdesk/internal memo** untuk menyortir prioritas.
- **Audit komunikasi personal** untuk mendorong etika dan efisiensi dalam penggunaan email korporat.

---

## 📜 Prompt History & Parameter Settings Explanation

### 🔄 Evolusi Prompt

#### ✅ Final Prompt
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

- ✅ Memberikan struktur jawaban yang **konsisten dan mudah di-parse**
- ✅ Meningkatkan akurasi klasifikasi karena format dipaksa eksplisit

### ⚙️ Model Settings (IBM Granite via Replicate)

| Parameter             | Value        | Reason                                                                 |
|-----------------------|--------------|------------------------------------------------------------------------|
| `max_new_tokens`      | 1000         | Cukup untuk summary + label                                           |
| `temperature`         | 0.2          | Output deterministik dan konsisten                                    |
| `top_p`               | 0.9          | Menjaga diversitas jawaban sambil menghindari noise                   |
| `top_k`               | 40           | Fokus pada token relevan                                              |
| `repetition_penalty` | 1.2          | Mencegah pengulangan frasa                                            |

Prompt dan parameter diuji coba secara iteratif untuk menghasilkan **hasil paling akurat, ringkas, dan bisa dikodekan secara downstream** (misalnya untuk analisis atau automasi).

---

## ✨ Credits

- Dataset dari [Kaggle - Enron Email Dataset](https://www.kaggle.com/datasets/wcukierski/enron-email-dataset)
- LLM inference via [Replicate API](https://replicate.com)
- Visualisasi dengan Python (Seaborn, Matplotlib)
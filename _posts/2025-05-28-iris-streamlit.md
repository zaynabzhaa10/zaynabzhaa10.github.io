---
title: Praktikum HDFS, Python, dan Streamlit di VS Code
layout: post
categories: [Blog, Tutorial]
tags: [HDFS, Python, Streamlit]
image:
  path: "/assets/streamlit.png"
---

# Praktikum HDFS, Python, dan Streamlit di VS Code

Dokumentasi ini merupakan bagian dari Praktikum Mata Kuliah **Big Data - Sistem Informasi - Universitas Hasanuddin 2025**. Tujuan dari praktikum ini adalah menghubungkan *dataset* yang disimpan di **HDFS**, mengolahnya dengan **Python**, dan menampilkan visualisasinya melalui **Streamlit**.

---

## Langkah-Langkah Praktikum

### 1. Instalasi Paket Python

Jalankan perintah berikut di terminal untuk menginstal semua pustaka yang diperlukan:

```bash
pip install streamlit pandas matplotlib seaborn plotly streamlit-option-menu
```

---

### 2. Instalasi Ekstensi di VS Code

Agar Streamlit dapat dijalankan langsung dari VS Code, pastikan kamu telah menginstal:

- **Ekstensi "Streamlit Runner"**  
  Digunakan untuk menjalankan file `.py` Streamlit langsung dari antarmuka VS Code.

#### Cara install:

1. Buka **Visual Studio Code (VS Code)**.
2. Pergi ke menu **Extensions** atau tekan `Ctrl + Shift + X`.
3. Di kolom pencarian, ketik: `Streamlit Runner`.
4. Klik tombol **Install**.

---

### 3. Persiapan Dataset

📥 **Download Dataset IRIS**  
Dataset asli dapat diunduh dari UCI Machine Learning Repository:

[🔗 Klik di sini untuk mengunduh iris.csv (iris.data)](https://archive.ics.uci.edu/ml/machine-learning-databases/iris/iris.data)

> **Catatan**: File ini tidak memiliki header. Tambahkan header berikut saat membacanya:
> `sepal_length, sepal_width, petal_length, petal_width, species`

Gunakan dataset `iris.csv` dan pastikan file tersebut sudah berada di dalam **HDFS**.
Untuk membaca file dari HDFS, gunakan kode berikut:

```python
import pandas as pd
from hdfs import InsecureClient

client = InsecureClient('http://localhost:9870', user='hadoop')
with client.read('/user/hadoop/iris.csv', encoding='utf-8') as reader:
    df = pd.read_csv(reader)
```

> 🔍 Pastikan `localhost:9870` dan path `/user/hadoop/iris.csv` sesuai dengan konfigurasi HDFS di komputermu.

---

### 4. Kode Aplikasi Streamlit

Buat file Python baru, misalnya `iris_app.py`, lalu isi dengan kode berikut:

```python
import streamlit as st
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from hdfs import InsecureClient

st.title("Visualisasi Dataset IRIS dari HDFS")

# Mengambil data dari HDFS
client = InsecureClient('http://localhost:9870', user='hadoop')
with client.read('/user/hadoop/iris.csv', encoding='utf-8') as reader:
    df = pd.read_csv(reader)

st.write("### Data Awal")
st.dataframe(df)

# Visualisasi
st.write("### Pairplot")
fig = sns.pairplot(df, hue="species")
st.pyplot(fig)
```

---

### ▶️ 5. Menjalankan Aplikasi Streamlit

Kamu bisa menjalankan aplikasi Streamlit dengan dua cara:

#### a. Melalui Terminal

```bash
streamlit run iris_app.py
```

#### b. Melalui VS Code (Jika menggunakan Streamlit Runner)

1. Buka file `iris_app.py`.
2. Klik tombol `▶️ Run` di pojok kanan atas editor.

---

### ✅ Final Words

Dengan menyelesaikan praktikum ini, kamu sudah:

- ✅ Mengakses data dari **HDFS**
- ✅ Membaca dan mengolah data menggunakan **Pandas**
- ✅ Membuat visualisasi menggunakan **Seaborn**
- ✅ Menampilkan hasil dalam antarmuka web interaktif menggunakan **Streamlit**

---
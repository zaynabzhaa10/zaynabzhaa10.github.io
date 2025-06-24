---
layout: post
title: "Tutorial Lengkap: Mengunduh dan Menyiapkan Apache Spark & Hadoop di Windows"
date: 2025-06-19 09:00:00 +0800 
categories: [Tutorial]
tags: [Apache Spark, Apache Hadoop, Instalasi Windows, Big Data, Data Engineering, Winutils]
author: Zainab
cover:
  image: /assets/images/Spark-Hadoop.png
  alt: "Cover Tutorial Spark-Hadoop"
---

# Tutorial Lengkap: Mengunduh dan Menyiapkan Apache Spark dan Apache Hadoop di Windows

Selamat datang di tutorial komprehensif ini! Jika Anda ingin menjelajahi dunia Big Data di sistem operasi Windows, **Apache Spark** dan **Apache Hadoop** adalah dua *framework* fundamental yang perlu Anda instal. Hadoop menyediakan fondasi untuk penyimpanan data terdistribusi (HDFS) dan pemrosesan awal, sementara Spark menawarkan kecepatan pemrosesan data yang jauh lebih tinggi dan fleksibilitas untuk analitik kompleks.

Tutorial ini akan memandu Anda melalui setiap langkah, mulai dari pengunduhan hingga penyiapan awal di lingkungan Windows Anda.

### Prasyarat Penting

Sebelum memulai, pastikan Anda sudah memenuhi prasyarat ini:

* **Koneksi Internet Aktif:** Diperlukan untuk mengunduh *file-file* yang berukuran besar.
* **Java Development Kit (JDK):** Versi 8 atau lebih baru. Spark dan Hadoop sangat bergantung pada Java.
    * **Pastikan JDK sudah terinstal dan variabel lingkungan `JAVA_HOME` sudah diatur dengan benar.** Anda bisa mengunduh JDK dari situs web Oracle atau OpenJDK.
    * Untuk memeriksa instalasi Java, buka Command Prompt (CMD) atau PowerShell dan ketik:
        ```cmd
        java -version
        javac -version
        ```
        Jika muncul informasi versi, berarti Java sudah terinstal. Jika tidak, Anda perlu menginstalnya terlebih dahulu dan mengatur `JAVA_HOME`.

---

## Langkah 1: Mengunduh Apache Hadoop

Apache Hadoop adalah kerangka kerja inti untuk penyimpanan data terdistribusi.

1.  **Kunjungi Halaman Unduh Resmi Apache Hadoop:**
    Buka *browser* Anda dan kunjungi alamat ini: [https://hadoop.apache.org/releases.html](https://hadoop.apache.org/releases.html)

2.  **Pilih Versi Stabil:**
    Di halaman rilis Hadoop, Anda akan melihat berbagai versi. **Selalu disarankan untuk memilih versi stabil dan terbaru** (misalnya, Hadoop 3.3.6 atau yang lebih baru saat ini). Cari bagian "**Binary**" untuk versi yang Anda inginkan.

    * Klik tautan **`binary`** di samping versi yang Anda pilih. Misalnya, jika Anda memilih versi 3.3.6, Anda akan mencari dan mengklik tautan seperti `hadoop-3.3.6/hadoop-3.3.6.tar.gz`.

3.  **Pilih *Mirror* Unduhan:**
    Setelah mengklik tautan `binary`, Anda akan diarahkan ke halaman yang menampilkan daftar *mirror* unduhan. Pilih salah satu *mirror* (biasanya yang terdekat dengan lokasi Anda) untuk memulai proses unduhan. *File* ini berukuran cukup besar (beberapa ratus MB), jadi mungkin perlu waktu.

4.  **Simpan *File*:**
    Buat folder baru di *drive* C: Anda, misalnya `C:\hadoop`. Kemudian, simpan *file* `hadoop-X.X.X.tar.gz` yang telah Anda unduh ke dalam folder ini.

---

## Langkah 2: Mengunduh Apache Spark

Apache Spark menawarkan pemrosesan data yang jauh lebih cepat dan cocok untuk analitik *real-time*.

1.  **Kunjungi Halaman Unduh Resmi Apache Spark:**
    Buka *browser* Anda dan kunjungi alamat ini: [https://spark.apache.org/downloads.html](https://spark.apache.org/downloads.html)

2.  **Konfigurasi Unduhan Spark:**
    Di halaman unduh Spark, Anda perlu memilih dua opsi penting:
    * **1. Choose a Spark release:** Pilih versi Spark terbaru yang stabil (misalnya, 3.5.1 atau yang lebih baru).
    * **2. Choose a package type:** Ini adalah bagian **paling penting**. Anda harus memilih *package* Spark yang **sudah dikompilasi dengan versi Hadoop yang kompatibel** dengan versi Hadoop yang baru saja Anda unduh.
        * Misalnya, jika Anda mengunduh **Hadoop 3.3.x**, pilih opsi seperti: `Pre-built for Apache Hadoop 3.3 and later`.
        * **Jangan** memilih opsi "Source Code" kecuali Anda memiliki alasan kuat untuk mengkompilasi Spark secara manual, yang jauh lebih kompleks.

3.  **Pilih *Mirror* Unduhan:**
    Setelah mengonfigurasi kedua opsi di atas, klik tautan unduhan yang akan muncul. Anda akan diarahkan ke halaman *mirror*. Pilih salah satu *mirror* untuk memulai unduhan.

4.  **Simpan *File*:**
    Buat folder baru di *drive* C: Anda, misalnya `C:\spark`. Kemudian, simpan *file* `spark-X.X.X-bin-hadoopY.Y.tgz` yang telah Anda unduh ke dalam folder ini.

---

## Langkah 3: Ekstraksi dan Penyiapan Awal

Setelah mengunduh kedua *file*, langkah selanjutnya adalah mengekstraknya dan menempatkannya di lokasi yang sesuai.

1.  **Ekstrak Hadoop:**
    * Pergi ke lokasi tempat Anda menyimpan `hadoop-X.X.X.tar.gz` (misalnya `C:\hadoop`).
    * Gunakan aplikasi seperti **7-Zip** atau **WinRAR** untuk mengekstrak *file*.
    * Pastikan Anda mengekstraknya sehingga folder `hadoop-X.X.X` berada langsung di dalam `C:\hadoop`. Jadi, jalur lengkapnya akan menjadi `C:\hadoop\hadoop-X.X.X`.

2.  **Ekstrak Spark:**
    * Pergi ke lokasi tempat Anda menyimpan `spark-X.X.X-bin-hadoopY.Y.tgz` (misalnya `C:\spark`).
    * Ekstrak *file* tersebut menggunakan 7-Zip atau WinRAR.
    * Pastikan folder yang diekstrak (misalnya `spark-X.X.X-bin-hadoopY.Y`) berada langsung di dalam `C:\spark`. Jadi, jalur lengkapnya akan menjadi `C:\spark\spark-X.X.X-bin-hadoopY.Y`.

3.  **Perbaikan `winutils.exe` (Penting untuk Windows):**
    Distribusi Hadoop di Windows tidak menyertakan *native binaries* seperti `winutils.exe` yang diperlukan untuk menjalankan beberapa fungsi Hadoop. Anda harus mengunduh *file* ini secara terpisah.
    * Kunjungi repositori GitHub yang berisi `winutils.exe` dan *file* pendukung lainnya: [https://github.com/steveloughran/winutils](https://github.com/steveloughran/winutils)
    * Navigasikan ke versi Hadoop yang Anda unduh (misalnya, `hadoop-3.3.x/bin`).
    * Unduh *file* `winutils.exe` dan `hadoop.dll` (jika tersedia untuk versi Anda) ke komputer Anda.
    * Buat folder `bin` di dalam folder instalasi Hadoop Anda, yaitu di `C:\hadoop\hadoop-X.X.X`.
    * Salin `winutils.exe` dan `hadoop.dll` (jika ada) yang baru Anda unduh ke dalam folder `C:\hadoop\hadoop-X.X.X\bin`.

---

## Langkah 4: Mengatur Variabel Lingkungan

Pengaturan variabel lingkungan sangat penting agar Windows dapat menemukan *file* eksekusi Hadoop dan Spark.

1.  **Buka Pengaturan Variabel Lingkungan:**
    * Cari "Environment Variables" di Start Menu Windows.
    * Pilih "Edit the system environment variables".
    * Di jendela "System Properties" yang muncul, klik tombol "**Environment Variables...**".

2.  **Buat Variabel Sistem Baru:**
    * Di bagian "System variables" (bukan "User variables"), klik tombol "**New...**".
    * **Untuk HADOOP:**
        * Nama Variabel: `HADOOP_HOME`
        * Nilai Variabel: `C:\hadoop\hadoop-X.X.X` (ganti `X.X.X` dengan versi Hadoop aktual Anda, misalnya `C:\hadoop\hadoop-3.3.6`)
    * **Untuk SPARK:**
        * Nama Variabel: `SPARK_HOME`
        * Nilai Variabel: `C:\spark\spark-X.X.X-bin-hadoopY.Y` (ganti `X.X.X-bin-hadoopY.Y` dengan nama folder Spark aktual Anda, misalnya `C:\spark\spark-3.5.1-bin-hadoop3`)
    * **Untuk JAVA_HOME (jika belum ada):**
        * Nama Variabel: `JAVA_HOME`
        * Nilai Variabel: `C:\Program Files\Java\jdk-X.X.X` (ganti `X.X.X` dengan versi JDK aktual Anda. Sesuaikan juga *path* jika JDK Anda diinstal di lokasi lain.)

3.  **Edit Variabel `Path`:**
    * Di daftar "System variables", cari variabel bernama "**Path**" dan klik tombol "**Edit...**".
    * Klik "**New**" dan tambahkan *path* berikut satu per satu:
        * `%HADOOP_HOME%\bin`
        * `%HADOOP_HOME%\sbin`
        * `%SPARK_HOME%\bin`
        * `%SPARK_HOME%\sbin`
        * `%JAVA_HOME%\bin` (penting agar perintah Java bisa dikenali)
    * Klik "**OK**" pada semua jendela yang terbuka untuk menyimpan semua perubahan.
    * **Sangat Penting:** Tutup semua jendela Command Prompt (CMD) atau PowerShell yang sedang terbuka, lalu buka kembali untuk menerapkan perubahan variabel lingkungan.

---

## Langkah 5: Verifikasi Instalasi

Setelah mengatur variabel lingkungan, saatnya memastikan Spark dan Hadoop sudah dikenali oleh sistem Windows Anda.

1.  **Buka Command Prompt (CMD) atau PowerShell Baru.**

2.  **Verifikasi Hadoop:**
    Ketik perintah berikut dan tekan Enter:
    ```cmd
    hadoop version
    ```
    Jika instalasi dan pengaturan `HADOOP_HOME` serta `Path` berhasil, Anda akan melihat informasi versi Hadoop yang terinstal.

3.  **Verifikasi Spark:**
    Untuk menguji Spark, kita bisa mencoba meluncurkan Spark Shell (lingkungan interaktif Spark):
    ```cmd
    spark-shell
    ```
    Jika semuanya benar, Spark Shell akan dimulai, dan Anda akan melihat *prompt* Scala (misalnya `scala>`). Untuk keluar dari Spark Shell, ketik `:quit` lalu tekan Enter.

    Anda juga bisa mencoba PySpark (untuk menggunakan Spark dengan Python, pastikan Python sudah terinstal):
    ```cmd
    pyspark
    ```

---

## Selamat!

Anda telah berhasil mengunduh dan melakukan penyiapan awal untuk Apache Spark dan Apache Hadoop di sistem Windows Anda.

Langkah selanjutnya biasanya melibatkan konfigurasi lebih lanjut untuk menjalankan Hadoop dalam mode *pseudo-distributed* (simulasi klaster di satu mesin) atau *fully-distributed* (klaster sesungguhnya), serta mulai menjalankan aplikasi Spark Anda. Proses ini akan melibatkan pengeditan *file-file* konfigurasi di dalam direktori `HADOOP_HOME\etc\hadoop` dan `SPARK_HOME\conf`.

Siap untuk melangkah lebih jauh ke konfigurasi dan penggunaan?
---
layout: post
title:  Grafika Komputer - Memuat Gambar dengan Pygame - P6
author: Ikhwan Elyas
description: Lanjutan Materi Grafika Komputer offline, Pada praktikum ini mahasiswa mempelajari dasar penggunaan Pygame load image, meliputi inisialisasi modul, pembuatan jendela tampilan, pengaturan warna, dan pemrosesan event agar aplikasi tidak langsung tertutup serta modifikasi code untuk dapat menampilkan gambar.
---


**Tujuan:**
Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:
1.  Memahami konsep `Surface` dalam Pygame.
2.  Menggunakan fungsi `pygame.image.load()` untuk memuat file gambar.
3.  Menampilkan gambar yang telah dimuat ke jendela Pygame menggunakan `blit()`.

---

### Dasar Teori

Dalam Pygame, semua elemen grafis yang ditampilkan seperti gambar, teks, atau bentuk, dianggap sebagai **Surface**. Anda bisa membayangkan `Surface` sebagai selembar kanvas kosong. Jendela utama aplikasi kita juga merupakan sebuah `Surface` khusus yang dibuat oleh `pygame.display.set_mode()`.

Untuk bekerja dengan gambar dari file (seperti .PNG, .JPG, .GIF), Pygame menyediakan modul `pygame.image`. Fungsi utama yang akan kita gunakan adalah:

`pygame.image.load("nama_file_gambar")`

Fungsi ini akan membaca file gambar dari disk dan membuat objek `Surface` baru yang berisi data piksel dari gambar tersebut. Setelah gambar berhasil dimuat ke dalam sebuah variabel (yang kini menjadi `Surface`), kita perlu "menggambarnya" ke `Surface` lain (yaitu layar utama) agar bisa terlihat. Proses menggambar satu `Surface` ke `Surface` lain ini disebut **blitting**.

---

### Langkah-langkah Praktikum

#### 1. Persiapan
- Buat sebuah folder baru untuk proyek praktikum ini.
- Siapkan sebuah file gambar (misalnya `kelinci.webp` atau `background.jpg`) dan letakkan di dalam folder yang sama dengan file Python Anda.

#### 2. Contoh Gambar Kelinci : 
![Gambar Kelinci](/gak/assets/img/p7-kelinci.webp){:width="150px" height="150px"}

#### 3. Kode Lengkap
Salin dan simpan kode berikut sebagai file Python (misalnya `praktikum6_load_image.py`):

```python
import pygame
import sys

# 1. Inisialisasi semua modul Pygame
pygame.init()

# 2. Pengaturan ukuran layar
lebar_layar = 800
tinggi_layar = 600
layar = pygame.display.set_mode((lebar_layar, tinggi_layar))
pygame.display.set_caption("Praktikum 6: Memuat Gambar")

# 3. Memuat gambar dari file
# Pastikan Anda memiliki file gambar di folder yang sama dengan kode ini.
# Ganti 'kelinci.webp' dengan nama file gambar Anda.
try:
    # pygame.image.load() akan mengembalikan sebuah Surface
    gambar_pemain = pygame.image.load('kelinci.webp').convert_alpha()
    gambar_pemain = pygame.transform.scale(gambar_pemain, (100,100))
except pygame.error as e:
    # Jika file tidak ditemukan, program akan keluar
    print(f"Error: Tidak dapat memuat gambar 'kelinci.webp'")
    print(e)
    sys.exit()


# 5. Game Loop (Perulangan Utama)
while True:
    # 6. Manajemen Event (Input dari user)
    for event in pygame.event.get():
        # Jika user menekan tombol close (X)
        if event.type == pygame.QUIT:
            pygame.quit() # Keluar dari Pygame
            sys.exit()    # Keluar dari program

    # 7. Logika dan Proses Menggambar
    # Atur warna latar belakang layar (misalnya, abu-abu muda)
    layar.fill((200, 200, 200))

    # "Blit" atau gambar Surface 'gambar_pemain' ke 'layar'
    # pada posisi yang ditentukan oleh 'posisi_gambar'
    layar.blit(gambar_pemain, (50,50))

    # 8. Update seluruh tampilan layar
    pygame.display.flip()

```

---

### Penjelasan Kode

1.  **`pygame.init()`**: Perintah wajib untuk menjalankan Pygame.
2.  **`pygame.display.set_mode(...)`**: Membuat jendela utama aplikasi. Ini adalah `Surface` utama tempat kita akan menggambar semua hal.
3.  **`pygame.image.load('gambar_saya.png')`**: Ini adalah fungsi inti dari praktikum ini. Ia mencari file bernama `gambar_saya.png` dan memuatnya sebagai `Surface` baru, yang kita simpan dalam variabel `gambar_pemain`.
4.  **`.convert_alpha()`**: Ini adalah optimasi. Fungsi ini mengubah format piksel gambar agar cocok dengan format piksel layar, sehingga proses `blit` akan berjalan jauh lebih cepat. Gunakan `.convert()` untuk gambar tanpa transparansi dan `.convert_alpha()` untuk gambar dengan transparansi (seperti file .PNG).
5.  **`gambar_pemain.get_rect(...)`**: Metode ini sangat berguna untuk mendapatkan objek `pygame.Rect` (persegi) dari sebuah `Surface`. `Rect` menyimpan informasi posisi (x, y) dan ukuran (lebar, tinggi) yang memudahkan kita untuk menempatkan gambar.
6.  **`layar.fill(...)`**: Mengisi `Surface` layar dengan satu warna solid. Ini dilakukan di setiap frame agar gambar dari frame sebelumnya terhapus.
7.  **`layar.blit(gambar_pemain, posisi_gambar)`**: Ini adalah proses menggambar. Perintah ini menyalin piksel dari `Surface` `gambar_pemain` ke `Surface` `layar` pada koordinat yang ditentukan oleh `posisi_gambar`.
8.  **`pygame.display.flip()`**: Setelah semua proses menggambar selesai dalam satu frame, perintah ini akan memperbarui seluruh layar untuk menampilkannya kepada pengguna.

---

### Latihan: 

1.  Gantilah file `'kelinci.webp'` dengan file gambar milik Anda. Jalankan program dan pastikan gambar Anda muncul di tengah layar.
2.  Ubah posisi gambar agar muncul di pojok kiri atas. (Petunjuk: koordinat pojok kiri atas adalah `(0, 0)`).
3.  Muatlah gambar kedua ke dalam variabel yang berbeda, dan tampilkan kedua gambar tersebut di layar pada posisi yang berbeda.

---
By: IkhwanElyas@fedora.linux
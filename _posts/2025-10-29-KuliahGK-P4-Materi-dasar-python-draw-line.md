---
layout: post
title:  Kuliah Grafika Komputer - Basic Draw Line - P4
author: Ikhwan Elyas
description: Lanjutan dalam bentuk Tugas, Pada praktikum ini mahasiswa mempelajari dasar penggunaan Pygame untuk grafika komputer, meliputi inisialisasi modul, pembuatan jendela tampilan, pengaturan warna, dan pemrosesan event agar aplikasi tidak langsung tertutup serta modifikasi code untuk praktik draw line.
---

## Pertemuan 4 – Tugas Pengganti 

### ✅ Panduan Menyimpan dan Menjalankan Program Python

1. Buka **Visual Studio Code** atau **Text Editor** favorit Anda.  
2. Buat file baru dengan nama:  
   **`praktikum4_tugas1_23001.py`**  
3. Simpan file tersebut di folder kerja, misalnya:  
   `/home/namauser/grafika/`
4. Atau jika di Windows, pilih folder `'Documents'`, misalnya:  
   `Documents\grafika\`
5. Jika sudah simpan filenya, `copy` code dibawah dan `paste` di **Text Editor** atau **Visual Studio Code**, kemudian simpan (tekan tombol: ctrl + s),
4. Setelah itu, Untuk menjalankan program, buka **Terminal**, lalu ketik perintah:

```bash
python3 praktikum4_tugas1_23001.py
```
atau jika menggunakan Windows:

```bash
#/perintah
python3 praktikum4_tugas1_23001.py
```

### ✅ TUGAS PENGGANTINYA: 

1. Silahkan anda `MODIFIKASI KODE` berikut agar dapat menghasilkan tampilan persis sebagaimana gambar berikut, lakukan Perubahan code dan jalankan lalu lihat hasilnya, jika belum sesuai lakukan perubahan code kembali sampai mendapatkan hasil seperti gambar dibawah: 

   ![Gambar Tugas1](/gak/assets/img/tugas1_gak.png)

2. Ukuran box (`display`) Menyesuaikan, `Backgroud-nya` warna `ke-Hijauan`, dan warna Garisnya `Kuning`, serta `posisi garis` ada di sebelah kanan (50 px dari kanan )

3. Jika sudah mendapatkan hasil tampilan yang sesuai dengan yang di gambar, silahkan `UPLOAD KODE-nya` sekalian `ABSEN` di `link` berikut: [[Absen dan Upload Tugas](https://gak.tifor.site/){:target="_blank"}] 


4. **Batas Isi Absen dan Upload File tugas hari ini (31/10/2025) Jam 00.00 (12 malam)**.

Berikut kode awal sebagai rujukan:
```python
import pygame
import sys

# Inisialisasi pygame
pygame.init()

# Membuat jendela (width x height)
screen = pygame.display.set_mode((400, 400))
pygame.display.set_caption("Contoh Garis di Pygame")

# Warna (R, G, B)
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Loop utama
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Isi background hitam
    screen.fill(BLACK)

    # Gambar garis putih
    pygame.draw.line(screen, WHITE, (50, 50), (200, 200), 3)

    # Update tampilan
    pygame.display.flip()

# Keluar
pygame.quit()
sys.exit()

```





---
By: elyas@fedora.linux

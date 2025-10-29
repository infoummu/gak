---
layout: post
title:  Kuliah Grafika Komputer - Basic Draw Line - P3
date:   2025-10-22 01:12:11 -0500
author: Ikhwan Elyas
description: Pada praktikum ini mahasiswa mempelajari dasar penggunaan Pygame untuk grafika komputer, meliputi inisialisasi modul, pembuatan jendela tampilan, pengaturan warna, dan pemrosesan event agar aplikasi tidak langsung tertutup. Mahasiswa juga belajar cara mengisi background serta menggambar objek grafis sederhana, yaitu garis, ke layar menggunakan koordinat 2D. Selain itu, dipahami pula pentingnya game loop dan pembaruan tampilan secara terus-menerus agar gambar dapat ditampilkan dengan benar.
---

## Pertemuan 3 – Praktikum Draw Line (Buat Garis)

### Panduan Menyimpan dan Menjalankan Program Python

1. Buka **Visual Studio Code** atau **Text Editor** favorit Anda.  
2. Buat file baru dengan nama:  
   **`praktikum3_line_23001.py`**  
3. Simpan file tersebut di folder kerja, misalnya:  
   `/home/namauser/grafika/`
4. Atau jika di Windows, pilih folder `'Documents'`, misalnya:  
   `Documents\grafika\`
5. Jika sudah simpan filenya, `copy` code dibawah dan `paste` di **Text Editor** atau **Visual Studio Code**, kemudian simpan (tekan tombol: ctrl + s),
4. Setelah itu, Untuk menjalankan program, buka **Terminal**, lalu ketik perintah:

```bash
python3 praktikum3_line_23001.py
```
atau jika menggunakan Windows:

```bash
#/perintah
python3 praktikum3_line_23001.py
```

### Praktikum 3 (22/10/2025)
Kode ini memperkenalkan konsep dasar tampilan grafis dalam Pygame: pembuatan jendela, sistem koordinat 2D, rendering objek grafis sederhana yaitu membuat garis, dan game loop untuk pembaruan layar secara terus-menerus.

Contoh kode:
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


### ✅ Apa yang dilakukan kode tersebut

- Mengimpor modul **Pygame** dan **sys** sebagai library untuk grafika dan fungsi sistem.
- Melakukan **inisialisasi Pygame** agar semua modul grafis siap digunakan.
- Membuat **jendela tampilan** berukuran 400×400 piksel dengan `pygame.display.set_mode()`.
- Memberi **judul jendela** menggunakan `pygame.display.set_caption()`.
- Mendefinisikan **warna** dalam format RGB (putih dan hitam).
- Menjalankan **loop utama (game loop)** agar program tetap berjalan sampai pengguna menutup jendela.
- Memproses **event**, khususnya `QUIT`, untuk keluar dari aplikasi dengan benar.
- Membersihkan layar dengan **background hitam** menggunakan `screen.fill()`.
- Menggambar **garis putih** ke layar menggunakan koordinat 2D.
- Memperbarui tampilan layar secara berkala dengan `pygame.display.flip()`.
- Mengakhiri program dengan benar menggunakan `pygame.quit()` dan `sys.exit()`.

### ✅ Latihan Lanjutan
1. Jika telah berhasil, silahkan lanjutkan dengan melakukan modifikasi pada code, agar paham dengan code yang ditulis
2. contoh pertama, ubah ukuran layar, `pygame.display.set_mode()` dari 400x400 menjadi 300x500, setelah itu jalankan dan lihat hasilnya.
3. kedua, ubah warna garis, `WHITE = (255, 255, 255)` dari putih menjadi biru `BLUE = (0, 0, 255)`
4. Selanjutnya, ubah bagian `gari` atau `line`, dan lakukan seterusnya seperti yang sudah `dijelaskan` dan `dicontohkan`.


---
By: elyas@fedora.linux

---
layout: post
title:  Kuliah Grafika Komputer - Basic Draw Circle - P5
author: Ikhwan Elyas
description: Lanjutan Materi Grafika Komputer offline, Pada praktikum ini mahasiswa mempelajari dasar penggunaan Pygame untuk grafika komputer untuk menggambar lingkaran, meliputi inisialisasi modul, pembuatan jendela tampilan, pengaturan warna, dan pemrosesan event agar aplikasi tidak langsung tertutup serta modifikasi code untuk praktik draw circle.
---



Di modul praktikum mata kuliah Grafika Komputer pada sesi kali ini, kita akan mempelajari cara menggambar objek dasar 2D, yaitu **lingkaran**, menggunakan library Pygame di Python.

## Tujuan Praktikum

- Mahasiswa mampu memahami konsep dasar menggambar objek di Pygame.
- Mahasiswa mampu menggunakan fungsi `pygame.draw.circle()` untuk membuat lingkaran.
- Mahasiswa dapat memodifikasi parameter seperti posisi, warna, dan ukuran lingkaran.

## Persiapan

Pastikan kamu sudah menginstall Python dan library Pygame di komputermu. Jika belum, buka terminal atau command prompt dan jalankan perintah:
```
pip install pygame
```

## Konsep Dasar: `pygame.draw.circle()`

Untuk menggambar sebuah lingkaran di Pygame, kita menggunakan fungsi yang sudah disediakan yaitu `pygame.draw.circle()`. Fungsi ini sangat mudah digunakan dan memiliki beberapa parameter penting.

Sintaks dasarnya adalah sebagai berikut:
```python
pygame.draw.circle(surface, color, center, radius, width=0)
```

Mari kita bedah setiap parameternya:
- `surface`: Ini adalah "kanvas" atau layar tempat kita akan menggambar. Biasanya ini adalah variabel yang kita buat untuk menampung window utama game.
- `color`: Warna lingkaran. Warna di Pygame didefinisikan dalam format RGB (Red, Green, Blue) dalam bentuk *tuple*, misalnya `(255, 0, 0)` untuk warna merah.
- `center`: Posisi pusat (tengah) dari lingkaran. Ini ditentukan dalam bentuk koordinat (x, y), misalnya `(100, 150)`.
- `radius`: Jari-jari lingkaran dalam satuan piksel. Semakin besar nilainya, semakin besar lingkarannya.
- `width` (opsional): Ketebalan garis tepi lingkaran.
    - Jika nilai `width` adalah `0` (atau tidak diisi), maka lingkaran akan terisi penuh dengan warna (solid).
    - Jika nilainya lebih besar dari `0` (misalnya `2`), maka Pygame akan menggambar lingkaran dengan garis tepi setebal 2 piksel, dan bagian dalamnya akan transparan.

---

## Contoh Kode Lengkap

Berikut adalah contoh kode lengkap untuk membuat sebuah window dan menggambar lingkaran merah di tengahnya.

```python
# Import library pygame
import pygame
import sys

# Inisialisasi Pygame
pygame.init()

# Ukuran window
screen_width = 800
screen_height = 600

# Membuat window
screen = pygame.display.set_mode((screen_width, screen_height))
pygame.display.set_caption("Praktikum 6: Menggambar Lingkaran")

# Definisi warna (RGB)
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Game loop utama
running = True
while running:
    # Event handler untuk menutup window
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # 1. Mengisi layar dengan warna latar belakang (putih)
    screen.fill(WHITE)

    # 2. Menggambar lingkaran
    # Parameter: (surface, color, center_position, radius)
    # Kita akan menggambar di tengah layar, jadi posisinya (width/2, height/2)
    center_x = screen_width // 2
    center_y = screen_height // 2
    pygame.draw.circle(screen, RED, (center_x, center_y), 50)

    # 3. Update display untuk menampilkan apa yang sudah digambar
    pygame.display.flip()

# Keluar dari Pygame
pygame.quit()
sys.exit()

```

### Penjelasan Kode:
1.  **Inisialisasi**: `pygame.init()` adalah perintah wajib untuk menyiapkan semua modul Pygame yang diperlukan.
2.  **Window Setup**: Kita menentukan ukuran layar dan membuat sebuah window dengan `pygame.display.set_mode()`.
3.  **Warna**: Kita mendefinisikan beberapa warna dasar dalam format RGB agar kode lebih mudah dibaca.
4.  **Game Loop**: `while running:` adalah loop utama tempat semua logika dan penggambaran terjadi. Loop ini akan terus berjalan sampai pengguna menutup window.
5.  **Event Handler**: Bagian `for event in pygame.event.get():` memeriksa setiap aksi dari pengguna, seperti menekan tombol atau mengklik mouse. Jika pengguna menekan tombol close (X), `pygame.QUIT` akan terdeteksi dan loop akan berhenti.
6.  **`screen.fill(WHITE)`**: Perintah ini membersihkan layar di setiap frame dengan memberinya warna putih. Ini penting agar gambar dari frame sebelumnya tidak menumpuk.
7.  **`pygame.draw.circle(...)`**: Inilah inti dari praktikum ini. Kita memanggil fungsi untuk menggambar lingkaran di `screen`, dengan warna `RED`, di posisi tengah layar, dan dengan radius `50` piksel.
8.  **`pygame.display.flip()`**: Setelah semua objek selesai digambar, perintah ini akan "membalik" layar untuk menampilkannya kepada pengguna. Bayangkan seperti menyelesaikan sebuah lukisan lalu menunjukkannya.
9.  **`pygame.draw.circle(screen, RED, (center_x, center_y), 50, 3)`**, tambahkan `3` untuk melihat hasil apa di layar ?


---

## Latihan

Untuk lebih memahami materi ini, coba modifikasi kode di atas untuk melakukan hal-hal berikut:

1.  **Ubah Posisi**: Pindahkan lingkaran ke pojok kiri atas layar. (Hint: ubah koordinat `center`).
2.  **Ubah Ukuran dan Warna**: Buat lingkaran menjadi lebih besar (misalnya radius 100) dan ubah warnanya menjadi biru.
3.  **Lingkaran Kosong**: Buat lingkaran kedua di samping lingkaran pertama, namun kali ini buat agar hanya garis tepinya yang terlihat (tidak solid). (Hint: tambahkan parameter `width`).

Silahkan mencoba dan bereksperimen!


---
By: IkhwanElyas@fedora.linux

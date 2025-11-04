---
layout: post
title:  Grafika Komputer - Memuat Gambar dengan Pygame - P7
author: Ikhwan Elyas
description: Lanjutan Materi Grafika Komputer offline, Pada praktikum ini mahasiswa mempelajari dasar penggunaan Pygame load image, meliputi inisialisasi modul, pembuatan jendela tampilan, pengaturan warna, dan pemrosesan event agar aplikasi tidak langsung tertutup serta modifikasi code untuk dapat menampilkan gambar.
---


## Manipulasi Gambar dengan Pygame
### Tujuan Praktikum
- Memahami cara memuat gambar menggunakan pygame.image.load()
- Mengatur ukuran gambar sesuai kebutuhan
- Menggabungkan beberapa gambar (background dan foreground)
- Mengimplementasikan manipulasi gambar dasar dengan Pygame

### Tools dan Library yang Diperlukan
- Python 3.x
- Pygame library
- Text editor (VS Code, PyCharm, atau lainnya)

### Contoh Gambar : 

1. Kelinci:
    ![Gambar Kelinci](/gak/assets/img/p7-kelinci.webp){:width="150px" height="150px"}{:target="_blank"}
2. Rumput: 
    ![Gambar Tugas1](/gak/assets/img/p7-grase.jpeg){:target="_blank"}

### Konsep Dasar
1. **Memuat Gambar dengan pygame.image.load()**
Fungsi ini digunakan untuk memuat gambar dari file ke dalam program.

```python
gambar = pygame.image.load('nama_file.jpg')
```

2. **Mengatur Ukuran Gambar**
Gambar dapat diubah ukurannya menggunakan pygame.transform.scale()

```python
gambar_baru = pygame.transform.scale(gambar, (lebar, tinggi))
```

3. **Menampilkan Gambar**
Gambar ditampilkan menggunakan blit() pada surface:

```python
screen.blit(gambar, (x, y))
```

Contoh Program Lengkap
```python
import pygame
import sys

# Inisialisasi Pygame
pygame.init()

# Set ukuran layar
SCREEN_WIDTH = 800
SCREEN_HEIGHT = 600
screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
pygame.display.set_caption("Praktikum 6 - Manipulasi Gambar")

# Warna
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Memuat gambar background
try:
    background = pygame.image.load('background.jpg')  # Ganti dengan path gambar Anda
    # Mengatur ukuran background sesuai layar
    background = pygame.transform.scale(background, (SCREEN_WIDTH, SCREEN_HEIGHT))
except:
    print("File background.jpg tidak ditemukan!")
    # Buat background default jika file tidak ditemukan
    background = pygame.Surface((SCREEN_WIDTH, SCREEN_HEIGHT))
    background.fill((100, 150, 200))  # Warna biru muda

# Memuat gambar foreground (karakter atau objek)
try:
    character = pygame.image.load('character.png')  # Ganti dengan path gambar Anda
    # Mengatur ukuran character
    character_width = 200
    character_height = 300
    character = pygame.transform.scale(character, (character_width, character_height))
except:
    print("File character.png tidak ditemukan!")
    # Buat karakter default jika file tidak ditemukan
    character = pygame.Surface((200, 300))
    character.fill((255, 0, 0))  # Warna merah

# Posisi character (di tengah layar)
character_x = (SCREEN_WIDTH - character.get_width()) // 2
character_y = (SCREEN_HEIGHT - character.get_height()) // 2

# Font untuk teks
font = pygame.font.Font(None, 36)

# Loop utama
running = True
clock = pygame.time.Clock()

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_ESCAPE:
                running = False
    
    # Menggambar background
    screen.blit(background, (0, 0))
    
    # Menggambar character di atas background
    screen.blit(character, (character_x, character_y))
    
    # Menambahkan teks informasi
    info_text = font.render("Praktikum 6 - Load Image dengan Pygame", True, BLACK)
    screen.blit(info_text, (50, 50))
    
    # Update display
    pygame.display.flip()
    
    # Mengatur FPS
    clock.tick(60)

# Keluar dari Pygame
pygame.quit()
sys.exit()
```

### Penjelasan Kode
1. **Inisialisasi Pygame**

    ```python
    pygame.init()
    ```
    - Menginisialisasi semua modul Pygame yang diperlukan

2. **Membuat Window**

    ```python
    screen = pygame.display.set_mode((SCREEN_WIDTH, SCREEN_HEIGHT))
    ```
    - Membuat window dengan ukuran yang ditentukan

3. **Memuat dan Mengatur Gambar**

    ```python
    background = pygame.image.load('background.jpg')
    background = pygame.transform.scale(background, (SCREEN_WIDTH, SCREEN_HEIGHT))
    ```
    - Memuat gambar dan mengubah ukurannya sesuai layar

4. **Error Handling**

    ```python
    try:
        # load gambar
    except:
        # buat gambar default
    ```    
    - Menangani error jika file gambar tidak ditemukan

5. **Game Loop**

    ```python
    while running:
        # event handling
        # drawing
        # update display
    ```
    Loop utama yang menangani input dan menampilkan gambar

### Langkah-langkah Praktikum
**Langkah 1: Persiapan File Gambar**
1. Siapkan dua gambar:
    - background.jpg (gambar landscape/latar belakang)
    - character.png (gambar objek/karakter dengan transparansi)

2. Letakkan gambar dalam folder yang sama dengan script Python

**Langkah 2: Implementasi Dasar**
1. Buat file Python baru
2. Copy kode contoh di atas
3. Sesuaikan nama file gambar dengan yang Anda miliki

**Langkah 3: Eksperimen**
1. Ubah ukuran karakter
2. Ubah posisi karakter
3. Coba tambahkan gambar ketiga
4. Eksperimen dengan efek transformasi lainnya

**Format Gambar yang Didukung**
- JPEG (.jpg, .jpeg)
- PNG (.png) - mendukung transparansi
- BMP (.bmp)
- GIF (.gif)

**Tips dan Best Practices**
- Gunakan PNG untuk gambar dengan transparansi
- Handle error ketika memuat gambar
- Scale gambar sesuai kebutuhan untuk optimasi performa
- Gunakan try-except untuk menangani file yang tidak ditemukan
- Bersihkan memory dengan `pygame.quit()`


**Troubleshooting:**

- `Masalah:` "File not found error"
- `Solusi:` Pastikan path gambar benar dan file ada di direktori yang tepat

- `Masalah:` Gambar terdistorsi
- `Solusi:` Pertahankan aspect ratio saat scaling

- `Masalah:` Performa lambat
- `Solusi:` Optimasi ukuran gambar dan gunakan gambar dengan resolusi sesuai kebutuhan


**Catatan:**
- Pastikan semua file gambar berada dalam direktori yang sama dengan script Python, atau berikan path yang benar ke file gambar tersebut.


---
By: IkhwanElyas@fedora.linux
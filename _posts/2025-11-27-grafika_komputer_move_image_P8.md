---
layout: post
title:  Grafika Komputer - Move Gambar Otomatis dan Keyboard - P8
author: Ikhwan Elyas
description: Lanjutan Materi Grafika Komputer offline, Pada praktikum ini mahasiswa mempelajari dasar penggunaan Pygame load image, meliputi inisialisasi modul, pembuatan jendela tampilan, pengaturan warna, dan pemrosesan event agar aplikasi tidak langsung tertutup serta modifikasi code untuk dapat menampilkan gambar.
---


* Menggerakkan Gambar secara Otomatis 
* Menggerakkan Gambar dengan Keyboard



### Contoh Gambar : 

1. Kelinci:
    ![Gambar Kelinci](/gak/assets/img/p7-kelinci.webp){:width="150px" height="150px"}{:target="_blank"}
2. Rumput: 
    ![Gambar Tugas1](/gak/assets/img/p7-grase.jpeg){:target="_blank"}
2. Wortel: 
    ![Gambar Tugas1](/gak/assets/img/wortel.png){:width="150px" height="150px"}{:target="_blank"}


### Move Gambar Otomatis

```python
import pygame
import sys

pygame.init()

lebar_layar = 800
tinggi_layar = 600
layar = pygame.display.set_mode((lebar_layar, tinggi_layar))
pygame.display.set_caption("Gerakan Kelinci: Kanan → Turun → Kiri → Naik")

# Muat gambar
try:
    gambar_pemain = pygame.image.load('kelinci.webp').convert_alpha()
    gambar_pemain = pygame.transform.scale(gambar_pemain, (100, 100))
except pygame.error as e:
    print("Error: Tidak dapat memuat gambar 'kelinci.webp'")
    print(e)
    sys.exit()

# posisi awal
x = 0
y = 0

# arah awal
arah = "kanan"

clock = pygame.time.Clock()

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    layar.fill((200, 200, 200))

    # ==========================
    # LOGIKA GERAK SESUAI INPUT
    # ==========================
    if arah == "kanan":
        x += 1
        if x >= 400:
            arah = "turun"  # pindah arah

    elif arah == "turun":
        y += 1
        if y >= 500:
            arah = "kiri"

    elif arah == "kiri":
        x -= 1
        if x <= 0:
            arah = "naik"

    elif arah == "naik":
        y -= 1
        if y <= 0:
            arah = "kanan"  # kembali ke kanan → loop ulang

    # gambar kelinci
    layar.blit(gambar_pemain, (x, y))

    pygame.display.flip()
    clock.tick(60)   # FPS biar tidak terlalu cepat

```


### Move Gambar dengan Keyboard 

```python
import pygame
import sys

pygame.init()

lebar_layar = 800
tinggi_layar = 600
layar = pygame.display.set_mode((lebar_layar, tinggi_layar))
pygame.display.set_caption("Gerakan Kelinci Dengan Keyboard")

# Muat gambar
try:
    gambar_pemain = pygame.image.load('kelinci.webp').convert_alpha()
    gambar_pemain = pygame.transform.scale(gambar_pemain, (100, 100))
except pygame.error as e:
    print("Error: Tidak dapat memuat gambar 'kelinci.webp'")
    print(e)
    sys.exit()

# posisi awal
x = 0
y = 0

kecepatan = 5
clock = pygame.time.Clock()

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # ==========================
    # INPUT KEYBOARD
    # ==========================
    tombol = pygame.key.get_pressed()

    if tombol[pygame.K_RIGHT]:   # panah kanan
        x += kecepatan

    if tombol[pygame.K_LEFT]:    # panah kiri
        x -= kecepatan

    if tombol[pygame.K_DOWN]:    # panah bawah
        y += kecepatan

    if tombol[pygame.K_UP]:      # panah atas
        y -= kecepatan

    # Batas layar (agar tidak keluar)
    if x < 0:
        x = 0
    if x > lebar_layar - 100:
        x = lebar_layar - 100

    if y < 0:
        y = 0
    if y > tinggi_layar - 100:
        y = tinggi_layar - 100

    # ==========================
    # GAMBARKAN
    # ==========================
    layar.fill((200, 200, 200))
    layar.blit(gambar_pemain, (x, y))

    pygame.display.flip()
    clock.tick(60)

```

### Move Dua Gambar (mini Game)

```python
import pygame
import sys
import random

pygame.init()

# Ukuran layar
lebar_layar = 800
tinggi_layar = 600
layar = pygame.display.set_mode((lebar_layar, tinggi_layar))
pygame.display.set_caption("Mini Game: Kelinci Makan Wortel")

# ==============================
# LOAD GAMBAR KELINCI
# ==============================
try:
    kelinci = pygame.image.load('kelinci.webp').convert_alpha()
    kelinci = pygame.transform.scale(kelinci, (100, 100))
except pygame.error as e:
    print("Error memuat kelinci.webp")
    print(e)
    sys.exit()

# ==============================
# LOAD GAMBAR WORTEL
# ==============================
try:
    wortel = pygame.image.load('wortel.png').convert_alpha()
    wortel = pygame.transform.scale(wortel, (70, 70))
except pygame.error as e:
    print("Error memuat wortel.png")
    print(e)
    sys.exit()

# Posisi awal objek
x = 100
y = 100

# Posisi awal wortel (acak)
wortel_x = random.randint(0, lebar_layar - 70)
wortel_y = random.randint(0, tinggi_layar - 70)

kecepatan = 5
clock = pygame.time.Clock()

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

    # ==========================
    # KONTROL KEYBOARD
    # ==========================
    tombol = pygame.key.get_pressed()

    if tombol[pygame.K_RIGHT]:
        x += kecepatan
    if tombol[pygame.K_LEFT]:
        x -= kecepatan
    if tombol[pygame.K_DOWN]:
        y += kecepatan
    if tombol[pygame.K_UP]:
        y -= kecepatan

    # Batas layar
    x = max(0, min(x, lebar_layar - 100))
    y = max(0, min(y, tinggi_layar - 100))

    # ==========================
    # CEK TABRAKAN (Collision)
    # ==========================
    kelinci_rect = kelinci.get_rect(topleft=(x, y))
    wortel_rect = wortel.get_rect(topleft=(wortel_x, wortel_y))

    if kelinci_rect.colliderect(wortel_rect):
        # Kelinci menyentuh wortel → pindahkan wortel ke posisi random
        wortel_x = random.randint(0, lebar_layar - 70)
        wortel_y = random.randint(0, tinggi_layar - 70)

    # ==========================
    # GAMBAR SEMUA OBJEK
    # ==========================
    layar.fill((230, 230, 230))

    layar.blit(wortel, (wortel_x, wortel_y))
    layar.blit(kelinci, (x, y))

    pygame.display.flip()
    clock.tick(60)

```
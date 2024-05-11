```bash 
import cv2 
import matplotlib.pyplot as plt
import numpy as np
```
import cv2: Ini mengimpor modul OpenCV, yang sering digunakan untuk bekerja dengan gambar, pemrosesan video, dan penglihatan komputer.

import matplotlib.pyplot as plt: Ini mengimpor modul pyplot dari pustaka Matplotlib, yang digunakan untuk membuat plot dan visualisasi data. Biasanya, modul ini diimpor dengan alias plt untuk memudahkan penggunaan.

import numpy as np: Ini mengimpor modul NumPy, yang merupakan pustaka populer untuk komputasi numerik di Python. NumPy digunakan untuk bekerja dengan array dan matriks, serta menyediakan fungsi-fungsi matematika yang kuat.

```bash 
foto = cv2.imread("rayyan.jpeg")
```
membaca gambar dengan nama file "rayyan.jpeg"
``` bash 
foto2 = cv2.cvtColor(foto, cv2.COLOR_BGR2RGB)
(baris, kolom) = foto.shape[:2]
plt.imshow(foto2)
```
foto = cv2.imread("rayyan.jpeg"): Ini membaca gambar dengan nama file "rayyan.jpeg" menggunakan fungsi imread() dari OpenCV. File gambar harus berada di direktori yang sama dengan skrip Python yang dieksekusi, atau path lengkap ke file gambar harus disediakan. Gambar dibaca dalam format default BGR (Blue-Green-Red) oleh OpenCV dan disimpan dalam variabel foto.

foto2 = cv2.cvtColor(foto, cv2.COLOR_BGR2RGB): Ini mengonversi gambar dari format warna BGR menjadi RGB menggunakan fungsi cvtColor() dari OpenCV. Matplotlib membutuhkan gambar dalam format RGB untuk menampilkan dengan benar. Hasilnya disimpan dalam variabel foto2.

(baris, kolom) = foto.shape[:2]: Ini mengambil dimensi gambar dalam bentuk (tinggi, lebar, channel) menggunakan atribut .shape dari array gambar foto, namun hanya menyimpan nilai tinggi dan lebarnya. Ini akan digunakan nanti untuk menentukan ukuran gambar yang akan ditampilkan.

plt.imshow(foto2): Ini menampilkan gambar yang sudah diubah formatnya (foto2) menggunakan fungsi imshow() dari Matplotlib. Karena gambar sudah dalam format RGB, akan ditampilkan dengan benar.

```bash 
for x in range(baris):
    for y in range(kolom):
        max1=0
        max2=0
        for z in range(3):
            if(max1==0):
                max1=foto2[x,y,z]
                imax1=z
            elif(max1<foto2[x,y,z]):
                max1=foto2[x,y,z]
                imax1=z
            elif(max2<foto2[x,y,z]):
                max2=foto2[x,y,z]
                imax2=z
        if((foto2[x,y,imax1]-foto2[x,y,imax2])>10):
            foto2[x,y,imax1]=foto2[x,y,imax1]-foto2[x,y,imax2]/2
            for z in range(3):
                if(z!=imax1):
                    foto2[x,y,z]=0

plt.imshow(foto2)
```
for x in range(baris):: Ini adalah loop yang iterasi melalui setiap baris dalam gambar.

for y in range(kolom):: Ini adalah loop bersarang yang iterasi melalui setiap kolom dalam gambar.

max1=0 dan max2=0: Variabel max1 dan max2 digunakan untuk melacak dua nilai tertinggi dalam piksel saat ini.

for z in range(3):: Ini adalah loop bersarang yang iterasi melalui tiga channel warna (diasumsikan RGB) dalam setiap piksel.

if(max1==0): ...: Ini adalah kondisi pertama yang menetapkan nilai max1 dan imax1 (indeks channel warna tertinggi pertama) jika max1 masih nol.

elif(max1<foto2[x,y,z]): ...: Jika nilai dalam channel warna saat ini lebih besar dari max1, maka nilai max1 dan imax1 diperbarui sesuai.

elif(max2<foto2[x,y,z]): ...: Jika nilai dalam channel warna saat ini lebih besar dari max2 tetapi lebih kecil dari max1, maka nilai max2 dan imax2 diperbarui.

if((foto2[x,y,imax1]-foto2[x,y,imax2])>10):: Setelah menemukan dua nilai tertinggi (max1 dan max2) untuk piksel saat ini, kondisi ini memeriksa apakah perbedaan antara kedua nilai tersebut lebih besar dari 10.

foto2[x,y,imax1]=foto2[x,y,imax1]-foto2[x,y,imax2]/2: Jika perbedaan antara kedua nilai tersebut lebih besar dari 10, maka nilai tertinggi pertama (max1) dikurangi setengah dari nilai tertinggi kedua (max2).

for z in range(3):: Ini adalah loop yang iterasi melalui tiga channel warna dalam piksel saat ini.

if(z!=imax1):: Kondisi ini memastikan bahwa nilai semua channel warna, kecuali yang memiliki nilai tertinggi pertama (max1), diatur menjadi 0.
``` bash 
merah=foto2[:,:,0]#merah
plt.imshow(merah, cmap='gray')
plt.colorbar()
plt.show()
```
merah=foto2[:,:,0]: Ini mengambil saluran merah dari setiap piksel dalam gambar foto2. Dalam representasi ini, sumbu pertama (':') merujuk pada seluruh baris gambar, sumbu kedua (':') merujuk pada seluruh kolom gambar, dan indeks '0' merujuk pada saluran merah. Jadi, variabel merah sekarang berisi saluran merah dari gambar foto2.

plt.imshow(merah, cmap='gray'): Ini menampilkan saluran merah yang sudah diambil sebagai gambar keabuan (grayscale) menggunakan fungsi imshow() dari Matplotlib. Dengan menyertakan argumen cmap='gray', itu memastikan bahwa gambar ditampilkan dalam skala abu-abu.

plt.colorbar(): Ini menambahkan colorbar ke plot, yang memberikan skala warna yang berkorespondensi dengan intensitas nilai piksel dalam gambar.

plt.show(): Ini menampilkan plot yang sudah disiapkan.
```bash 
hijau = foto2[:,:,1]#hijau
plt.imshow(hijau, cmap='gray')
plt.colorbar()
plt.show()
```
hijau = foto2[:,:,1]: Ini mengambil saluran hijau dari setiap piksel dalam gambar foto2. Dalam representasi ini, sumbu pertama (':') merujuk pada seluruh baris gambar, sumbu kedua (':') merujuk pada seluruh kolom gambar, dan indeks '1' merujuk pada saluran hijau. Jadi, variabel hijau sekarang berisi saluran hijau dari gambar foto2.
```bash 
biru=foto2[:,:,2] #Biru
plt.imshow(biru, cmap='gray')
plt.colorbar()
plt.show()
```
biru=foto2[:,:,2]: Ini mengambil saluran biru dari setiap piksel dalam gambar foto2. Dalam representasi ini, sumbu pertama (':') merujuk pada seluruh baris gambar, sumbu kedua (':') merujuk pada seluruh kolom gambar, dan indeks '2' merujuk pada saluran biru. Jadi, variabel biru sekarang berisi saluran biru dari gambar foto2.
``` bash 
merah=foto2[:,:,0] #Merah
hijau=foto2[:,:,1] #Hijau
biru=foto2[:,:,2] #Biru

fig, axs= plt.subplots(3,2, figsize=(15,5))
axs[0,0].imshow(merah, cmap='gray')
axs[0,1].hist(merah.ravel(), 256, [0,256])
axs[1,0].imshow(hijau, cmap='gray')
axs[1,1].hist(hijau.ravel(), 256, [0,256])
axs[2,0].imshow(biru,cmap='gray')
axs[2,1].hist(biru.ravel(), 256, [0,256])
plt.show()

```
merah=foto2[:,:,0], hijau=foto2[:,:,1], biru=foto2[:,:,2]: Ini mengambil saluran merah, hijau, dan biru dari setiap piksel dalam gambar foto2, masing-masing disimpan dalam variabel merah, hijau, dan biru.

fig, axs = plt.subplots(3, 2, figsize=(15, 5)): Ini membuat objek gambar (fig) dan array subplot (axs) dengan ukuran 3 baris dan 2 kolom. Ukuran total gambar ditentukan oleh figsize=(15, 5), yang mengatur lebar menjadi 15 inci dan tinggi menjadi 5 inci.

axs[0,0].imshow(merah, cmap='gray'): Ini menampilkan subplot pertama (baris ke-1, kolom ke-1) dengan saluran merah menggunakan imshow().

axs[0,1].hist(merah.ravel(), 256, [0,256]): Ini menampilkan histogram untuk saluran merah dalam subplot pertama, menggunakan hist() untuk menghitung frekuensi intensitas piksel. Argumen ravel() digunakan untuk meratakan matriks saluran merah menjadi larik satu dimensi. Argumen kedua 256 menunjukkan jumlah bin histogram, dan argumen ketiga [0,256] menunjukkan rentang nilai intensitas yang akan dihitung dalam histogram.

Langkah-langkah 3 dan 4 di atas diulangi untuk saluran hijau dan biru, masing-masing menampilkan gambar dan histogramnya di subplot kedua dan ketiga.

plt.show(): Ini menampilkan semua subplot yang sudah disiapkan.

``` bash 
gray = cv2.cvtColor(foto2, cv2.COLOR_RGB2GRAY)
fig, axs = plt.subplots (2, 2, figsize=(10,10))

(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')

(thresh, binary2) = cv2.threshold(gray, 10, 255, cv2.THRESH_BINARY)
axs[0,1].imshow(binary2, cmap = 'binary')
axs[0,1].set_title('BLUE')

(thresh, binary3) = cv2.threshold(gray, 50, 255, cv2.THRESH_BINARY)
axs[1,0].imshow(binary3, cmap = 'binary')
axs[1,0].set_title('RED-BLUE')

(thresh, binary4) = cv2.threshold(gray, 90, 255, cv2.THRESH_BINARY)
axs[1,1].imshow(binary4, cmap = 'binary')
axs[1,1].set_title('RED-GREEN-BLUE')

```
gray = cv2.cvtColor(foto2, cv2.COLOR_RGB2GRAY): Ini mengonversi gambar foto2 dari mode warna RGB ke skala abu-abu (grayscale) menggunakan fungsi cvtColor() dari OpenCV. Hasilnya disimpan dalam variabel gray.

fig, axs = plt.subplots(2, 2, figsize=(10,10)): Ini membuat objek gambar (fig) dan array subplot (axs) dengan ukuran 2 baris dan 2 kolom. Ukuran total gambar ditentukan oleh figsize=(10, 10), yang mengatur lebar dan tinggi gambar menjadi 10 inci.

(thresh, binary1) = cv2.threshold(gray, 0, 0, cv2.THRESH_BINARY): Ini menggunakan fungsi threshold() dari OpenCV untuk menerapkan ambang binary ke gambar gray. Pada subplot pertama (baris ke-1, kolom ke-1), gambar biner diterapkan tanpa ambang (nilai ambang bawah dan atas adalah 0), yang artinya seluruh piksel yang bernilai di atas ambang akan menjadi 255, sedangkan yang di bawah akan menjadi 0. Hasilnya disimpan dalam variabel binary1.

Langkah-langkah 3-6 di atas diulangi untuk menerapkan ambang binary dengan nilai ambang yang berbeda ke gambar gray, dan hasilnya disimpan dalam variabel binary2, binary3, dan binary4. Setiap subplot diberi judul yang sesuai dengan nilai ambang yang digunakan.

axs[baris, kolom].imshow(binary, cmap='binary'): Ini menampilkan gambar biner dalam subplot yang sesuai. Argumen cmap='binary' mengatur colormap menjadi biner, di mana piksel bernilai 0 akan menjadi hitam dan piksel bernilai 255 akan menjadi putih.

axs[baris, kolom].set_title('Judul'): Ini menambahkan judul pada setiap subplot untuk menjelaskan nilai ambang yang digunakan.

```bash 
r = foto2[:, :, 0]
g = foto2[:, :, 1]
b = foto2[:, :, 2]
color_image = cv2.imread('rayyan.jpeg')

histogram_biru = cv2.calcHist([b], [0], None, [256], [0, 256])
histogram_hijau = cv2.calcHist([g], [0], None, [256], [0, 256])
histogram_merah = cv2.calcHist([r], [0], None, [256], [0, 256])
histogram_warna = cv2.calcHist([color_image], [0], None, [256], [0, 256])

plt.figure(figsize=(12, 8))
plt.subplot(2, 2, 1)  # Subplot 1 (atas kiri)
plt.plot(histogram_biru, color='b')
plt.title('Histogram Biru')
plt.xlim([0, 256])

plt.subplot(2, 2, 2)  # Subplot 2 (atas kanan)
plt.plot(histogram_hijau, color='g')
plt.title('Histogram Hijau')
plt.xlim([0, 256])

plt.subplot(2, 2, 3)  # Subplot 3 (bawah kiri)
plt.plot(histogram_merah, color='r')
plt.title('Histogram Merah')
plt.xlim([0, 256])


plt.subplot(2, 2, 4)  # Subplot 4 (bawah kanan)
plt.plot(histogram_warna.flatten(), color='gray')  # Flatten histogram multi-dimensi
plt.title('Histogram Warna')
plt.xlim([0, 256])
```
r = foto2[:, :, 0], g = foto2[:, :, 1], b = foto2[:, :, 2]: Ini memisahkan saluran warna merah, hijau, dan biru dari gambar foto2 dan menyimpannya dalam variabel r, g, dan b masing-masing.

color_image = cv2.imread('rayyan.jpeg'): Ini membaca kembali gambar asli dengan menggunakan OpenCV dan menyimpannya dalam variabel color_image. Kita akan menggunakan ini untuk menghitung histogram keseluruhan warna.

histogram_biru = cv2.calcHist([b], [0], None, [256], [0, 256]): Ini menghitung histogram untuk saluran biru (b) menggunakan fungsi calcHist() dari OpenCV. Histogram tersebut disimpan dalam variabel histogram_biru. Argument [b] menunjukkan bahwa kita ingin menghitung histogram dari saluran biru. Argument [0] menunjukkan saluran yang ingin dihitung (dalam hal ini, saluran 0). Argumen None menunjukkan bahwa kita tidak menggunakan maska. Argumen [256] menunjukkan jumlah bin histogram, dan argumen [0, 256] menunjukkan rentang nilai intensitas yang akan dihitung dalam histogram.

Langkah-langkah 3 di atas diulangi untuk menghitung histogram dari saluran hijau (histogram_hijau) dan saluran merah (histogram_merah) dengan memanfaatkan variabel g dan r.

histogram_warna = cv2.calcHist([color_image], [0], None, [256], [0, 256]): Ini menghitung histogram keseluruhan warna menggunakan gambar asli (color_image). Histogram tersebut disimpan dalam variabel histogram_warna.

plt.figure(figsize=(12, 8)): Ini membuat sebuah figur dengan ukuran 12x8 inci.

plt.subplot(2, 2, 1), plt.subplot(2, 2, 2), plt.subplot(2, 2, 3), plt.subplot(2, 2, 4): Ini membuat empat subplot dalam figur tersebut. Subplot 1, 2, dan 3 menampilkan histogram saluran warna biru, hijau, dan merah masing-masing, sementara subplot 4 menampilkan histogram keseluruhan warna.

plt.plot(histogram_biru, color='b'), plt.plot(histogram_hijau, color='g'), plt.plot(histogram_merah, color='r'): Ini menggambar plot histogram untuk saluran biru, hijau, dan merah masing-masing. Warna plot ditentukan oleh argumen color, yaitu 'b' untuk biru, 'g' untuk hijau, dan 'r' untuk merah.

plt.plot(histogram_warna.flatten(), color='gray'): Ini menggambar plot histogram keseluruhan warna. Karena histogram keseluruhan adalah array multi-dimensi, kita harus meratakan histogramnya menggunakan flatten() sebelum memplotnya. Warna plot ditentukan oleh argumen color, yaitu 'gray'.

plt.title(), plt.xlim(): Ini menambahkan judul pada setiap subplot dan menetapkan batas sumbu x untuk setiap plot histogram.


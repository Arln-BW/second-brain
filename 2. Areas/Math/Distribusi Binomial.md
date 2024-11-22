---
tags:
  - math
Links: "[[Science Lessons]]"
---

[Latex](https://en.wikibooks.org/wiki/LaTeX/Mathematics)
# A. Variabel Acak
---
## 1. Percobaan Acak
Percobaan adalah suatu tindakan atau kegiatan untuk memperoleh hasil tertentu. contoh : 

>**Percobaan** melempar sebuah koin
>**Hasil** muncul angka atau gambar

Percobaan Acak adalah percobaan yang dapat diulang denan kondisi yang sama, dengan kemungkinan hasil yang selalu tetap

>[!NOTE] 
>Kepastian hasil yang muncul tidak diketahui secara pasti, namun kemungkinan hasil yang akan muncul dapat diketahui

## 2. Variabel Acak
Suatu variabel yang memetakan anggota ruang sampel ke anggota himpunan bilangan real.

>[!NOTE]
>Variabel acak disimbolkan dengan huruf kapital seperti : $X, Y, C$ dan sebagainya

## 3. Variabel Acak Diskrit

Variabel acak yang tidak mengambil seluruh nilai yang ada dalam sebuah interval atau variabel yang hanya memiliki nilai tertentu misalnya bilangan bulat. 
Contoh : variabel acak $X$ menyatakan banyaknya angka uang muncuk pada pelemparan sebuah koin.
- $X = 1$, jika 1 angka yang muncul
- $X = 0$, jika tidak ada angka yang muncul

>[!NOTE]
>Variabel acak diskrit dapat dihitung dan tidak membentuk interval

---
# B. Distibusi Probabilitas Diskrit

## 1. Probabilitas Diskrit

Suatu distribusi yang memuat data semua kemungkinan nilai variabel acak diskrit dan nilai probabilitasnya.
Contoh Soal :
Daari dalam kotak berisi 5 kelereng biru dan 3 kelereng hijau. Akan diambil 2 kelereng sekaligus secara acak. Jika varibel acak $X$ menyatakan banyaknya kelereng hijau yang terambil, maka distribusi probabilitas untuk variabel acak $X$ adalah ...
- $X = 0$, jika kelereng hijau yang tidak terambil
- $X = 1$, jika terambil 1 kelereng hijau
- $X = 2$, jika terambil 2 kelereng hijau
>[!CAUTION] Selesaikan

---
# C. Ekspektasi dan Variansi Diskrit

## 1. Ekspektasi Variabel Acak Diskrit $X$ $[E(X) \hspace{1mm} atau \hspace{1mm} \mu]$
Suatu rata-rata janka panjang dari suatu variabel acak. Rumus : $$\mu=E(X)=\displaystyle\sum_{i=1}^{n} (x_i.P(X=x_i))$$Misalkan dua koin delempar secara bersamaan sebanyak 10 kali. $X$ merupakan banyaknya gambar yang muncul pada pelemparan dua koin dan disajikan dalam tabel berikut ini :

| $x_i$ | $f_i$ |
| :---: | :---: |
|   0   |   1   |
|   1   |   6   |
|   2   |   3   |
$$\bar{x}=\frac{\displaystyle\sum_{i=1}^{n} (x_i.f_i)}{f_{total}} = 0.\frac{1}{10}+1.\frac{6}{10}+2.\frac{3}{10}$$
$$\implies x_1.\frac{f_1}{10}+x_2.\frac{f_2}{10}+x_3.\frac{f_3}{10}$$
$$\implies \displaystyle\sum_{i=1}^{n}(x_i.\frac{f_i}{10})$$
Contoh Soal : Sebuah kotak berisi 3 bola merah, 5 bola kuning dan 2 bola biru. Akan diambil satu bola secara acak dari kotak. Hadiah akan diberikan dengan ketentuan sebagai berikut.
- 10.000 rupiah ketika bila merah yang diambil
- 5.000 rupiah ketika bola kuning yang diambil
- 100.000 rupiah ketika bola biru yang diambil
Berapa rata-rata hadiah yang didapatkan dalam 1 pengambilan.

|   $x$    |     10.000     | 5.000            | 100.000          |
| :------: | :------------: | :--------------: | :--------------: |
| $P(X=x)$ | $\frac{3}{10}$ | $\frac{5}{10}$   | $\frac{2}{10}$   |

>[!CAUTION] Selesaikan

>[!NOTE] Bentuk Lain
>Terkadang Ekspektasi Fungsi $X$ ditanyakan dalam bentuk lain seperti : $E(X^2),\hspace{1mm} E(3X+5), \hspace{1mm} E(X^2+2X+4)$. Cara mengerjakannya dengan jumlahan dari nilai fungsi dikalikan peluangnya. Contoh : $E(X^2+2X)=\displaystyle\sum_{i=1}^{n}(({x_i}^2+2x_i).P(X=xi))$


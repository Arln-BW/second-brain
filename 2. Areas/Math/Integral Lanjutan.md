---
tags:
  - math
Links: "[[Science Lessons]]"
---
---
[Latex](https://en.wikibooks.org/wiki/LaTeX/Mathematics)
## Rumus Integral Tentu

$$\int\limits_a^b f(x)dx = [F(x)]_0^1 = F(b)-F(a)$$
___
## Menentukan Luas di Bawah Grafik

Untuk menentukan luas di bawah grafik, misal fungsi $f(x)$. Perlu dibutuhkan sebuah konsep dengan menggunakan persegi panjang yang cukup banyak dan menutupi area pada grafik $f(x)$ yang ingin ditentukan luasnya. Riemann Formula adalah konsep dari persegi panjang yang menutupi luas area grafik yang ingin ditentukan. Rumus Jumlah Riemann :

$$\int\limits_a^b f(x)d x=\lim\limits_{n \to \infty}\displaystyle\sum_{i=1}^{n}f(x_i).\Delta x,\hspace{1.5mm} \Delta x=\frac{b-a}{n}$$
### 1. Luas Persegi Panjang

$$\Delta F(x) = \Delta x.f(x) \implies \frac{\Delta F(x)}{\Delta x}=f(x)$$
### 2. Membuat persegi panjang di area yang ingin diketahui besar luasnya

$$\lim\limits_{\Delta x \to 0}\bigg[\frac{\Delta F(x)}{\Delta x}\bigg] =f(x) \implies \frac{d}{dx}F(x)=f(x) \implies F(x)=\int f(x) dx$$


>[!NOTE]
>Buat persegi panjang yang banyak sampai tak hingga dan $\bigtriangleup x \approx 0$

Sehingga didapatkan kesimpulan sebagai berikut :

$$F(x)=\int_{-\infty}^b f(x)dx$$

### 3. Bukti Rumus Integral Tentu

$\int_a^b f (x)$ $dx$ Memiliki arti Luas daerah di bawah f(x) tetapi di atas sumbu-x dengan batas $x = a$ sampai $x = b$. Penerapan : 

$\to$ $A_1=F(x)=\int_{-\infty}^b f(x)dx$

$\to$ $A_1=F(x)=\int_{-\infty}^a f(x)dx$

$\to$ $A=A_2-A_1$ $\implies A = F(b)-F(a)$

$\to$ $\int\limits_a^b f(x)dx = F(b)-F(a)$

---
## Sifat-Sifat Integral Tentu
### 1. Batas Bawah Sama dengan Batas Atas

$$\int\limits_a^a f(x)dx = 0 \implies \int\limits_a^a f(x)dx = F(a)-F(a)$$
### 2. Batas Bawah Bertukar dengan Batas Atas

$$\int\limits_a^b f(x)dx = -\int\limits_b^a f(x)dx$$
Pembuktian :

$\Rightarrow \int\limits_a^b f(x)dx = F(b)-F(a) = -[F(a)-F(b)]$
$\Rightarrow -[F(a)-F(b)]= -\int\limits_b^a f(x)dx$
### 3. Batas Bawah Berlawanan dengan Batas Atas
#### $a.$ $f(x)$ Fungsi Ganjil
$$\int\limits_{-a}^a f(x)dx = 0$$
>[!NOTE] Syarat Fungsi Ganjil
>Fungsi yang simetris terhadap titik asal $O(0,0)$. Secara matematis dapat ditulis $f(-x)=-f(x)$ untuk semua nilai $x$. Contoh : $f(x)=x$
#### $b.$ $f(x)$ Fungsi Genap
$$\int\limits_{-a}^a f(x)dx = 2\int\limits_{0}^a f(x)dx$$
>[!NOTE] Syarat Fungsi Genap
>Fungsi yang simetris terhadap sumbu-$y$. Secara matematis dapat ditulis $f(-x)=f(x)$ untuk semua nilai $x$. Contoh : $f(x)=x^2$
### 4. Batas Bawah dan Batas Atas Terpisah oleh Batas Lain
$$\int\limits_a^b f(x)dx = \int\limits_a^c f(x)dx \hspace{1mm} + \hspace{1mm} \int\limits_c^b f(x)dx$$
### 5. Penjumlahan & Pengurangan

$$\int\limits_a^b (f(x)+g(x))dx = \int\limits_a^b f(x)dx \hspace{1mm} + \hspace{1mm} \int\limits_a^b g(x)dx$$

$$\int\limits_a^b (f(x)-g(x))dx = \int\limits_a^b f(x)dx \hspace{1mm} - \hspace{1mm} \int\limits_a^b g(x)dx$$

---
## Metode Subtitisi pada Integral Tentu
1. Tentukan fungsi yang akan disubsitusi dan misalkan dengan $u$.
2. Tentukan turunan pertama dari $u$ sehinga didapatkan bentuk $du$
3. Ubah batas integral dari $x$ ke $u$
4. Subsitusikan hasil dari langkah 1, 2, dan 3 ke integral awal
5. Integralkan hasil dari langkah 4
---
## Integral Parsial (Partition)
Penurunan rumus integral parsial berasal dari fungsi $u=f(x)$ dan $v=g(x)$
1. Turunan dari $u.v$
$$\frac{d(uv)}{dx}=u\frac{dv}{dx}+\frac{du}{dx}v$$
2. Integralkan terhadap $x$
$$\to \int \frac{d(uv)}{dx}\hspace{1.5mm}dx=\int u\frac{dv}{dx}\hspace{1.5mm}dx+\int v\frac{du}{dx}\hspace{1.5mm}dx$$
$$\to uv=\int u\frac{dv}{dx}\hspace{1.5mm}dx+\int v\frac{du}{dx}\hspace{1.5mm}dx$$
$$\to uv-\int v\frac{du}{dx}\hspace{1.5mm}dx=\int u\frac{dv}{dx}\hspace{1.5mm}dx$$
3. Sehingga formulanya
$$\int u\frac{dv}{dx}\hspace{1.5mm}dx=uv-\int v\frac{du}{dx}\hspace{1.5mm}dx$$


>[!WARNING] Note :
>Ubah pemisalan ke bentuk aljabar yang paling sederhana sebagai $u$ dan bagian lain sebagai $\frac{dv}{dx}$. Cara lain ada *Metode Tanzalin*


Contoh : $\int 2x(2x-5)^3\hspace{1.5mm}dx=...$

>[!NOTE] Note :
>$$\int (ax+b)^n\hspace{1mm}dx=\frac{1}{a(n+1)}(ax+b)^{n+1}+C$$

---

>[!NOTE] Note :
>$$\int ax^n\hspace{1mm}dx=\frac{a}{(n+1)}x^{n+1}+C$$


---
tags:
  - physics
Time: 2024-11-04T06:52:00
Links: "[[Science Lessons]]"
---
---
## A. Pendahuluan Fluida Ideal & Fluida Dinamis
### 1. Fluida Ideal
Fluida memiliki sifat yang kompleks sehingga sulit untuk bisa dipelajari secara langsung. Oleh karena itu, fluida yang dipelajari atau diamati harus disederhanakan atau bisa disebut dengan *Fluida Ideal*. Ada pula sifat yang terdapat pada fluida ideal antara lain :
#### a. Aliran bersifat laminar/aliran garis lurus
Aliran fluida halus, sejajar dan tidak berputar atau tidak turbulen. Fluidanya mengalir sejajar dan jelas ujung dan pangkalnya
#### b. Fluida tidak kompresibel
Fluida yang mengalir tidak mengalami perubahan volume atau massa jenis jika ditekan atau diberi beban.

Densitas fluida konstan dan tidak dipengaruhi oleh besar tekanan.
#### c. Fluida bersifat tunak (Steady)
Kecepatan fluida di suatu titik selalu konstan terhadap waktu, sehingga jumlah fluida yang masuk sama dengan fluida yang keluar
#### d. Viskositas fluida dinggap nol atau Tidak kental(non-viscous)
Contohnya madu dikatakan lebih viskos dari pada air
### 2. Fluida Dinamis
__Fluida__ didefinisikan sebagai zat yang akan mengalami deformasi atau perubahan struktur dan bentuk secara kontinyu saat diberikan tegangan geser.

Secara sederhana __Fluida__ didefinisikan sebagai zat yang bisa mengalir dan berubah bentuk sesuai wadahnya.

__Fluida Dinamis__ adalah ilmu yang memperlajari tentang sifat fluida yang bergerak dan pengaruhnya terhadap besaran-besaran lain.

### 3. Aliran Fluida

#### a. Aliran Laminer
Aliran yang bergerak dalam lapisan lapisan yang sejajar (*streamline*) serta tidak saling berpotongan atau berputar (*turbulen*).

#### b. Aliran Turbulen
Aliran yang bergerak tidak saling teratur antar garis arusnya, saling bertabrakan atau menumbuk sehingga terjadi turbulensi atau pusaran pada fluida

#### c. Aliran Transisi
Aliran yang merupakan peralihan dari aliran laminer ke turbulen maupun sebaliknya.

### 4. Bilangan Reynolds
Bilangan Reynolds merupakan bilangan tak berdimensi yang dapat membedakan suatu aliran itu dinamakan laminer, transisi, atau turbulen. $$Re=\frac{\rho v d}{\mu}$$
> [!NOTE] Keterangan
> - $Re$ : Bilangan Reynolds
> - $\rho$ : massa jenis ($kg/m^3$)
> - $v$ : kecepatan fluida (m/s)
> - $d$ : diameter pipa (jika penampang pipa lingkaran) (m)
> - $\mu$ : viskositas ($kg/ms$)

> [!WARNING] NOTES
> - $Re < 2300$ : aliran laminar
> - $2300 < Re < 4000$ : aliran transisi
> - $Re > 4000$ : aliran turbulen
## B. Kontinuitas

### 1. Debit
Debit adalah volume atau massa fluida yang mengalir dalam setiap waktu. Deit juga menyatakan besarnya laju volume fluida yang mengalir melalui suatu penampang tertentu. Debit dapat dihitung menggunakan persamaan :

![[pipa1.png#center|350]]
$$Q=\frac{V}{t}$$
$$Q=A.v$$

> [!NOTE] Keterangan
> - $Q$ : Debit ($m^3/s$)
> - $V$ : volume fluida ($m^3$)
> - $t$ : selang waktu ($s$)
> - $A$ : Luas penampang ($m^2$)
> - $v$ : kecepatan fluida ($m/s$)

### 2. Asas Kontinuitas Pertama

![[pipa2.png#center|400]]

Debit fluida dalam pipa yang mengalir dalam 1 aliran akan selalu tetap. Meskipun keadaan geometri pipa berubah. Artinya meskipun luas penampang pipa berubah debit aliran akan selalu tetap. Dapat dirumuskan sebagai berikut : $$\to Q_1=Q_2$$$$\to \frac{\Delta V_1}{\Delta t_2}=\frac{\Delta V_1}{\Delta t_2}$$$$\to v_1.A_1 = v_2.A_2$$$$\to v_1(r_1)^2 = v_2(r_2)^2$$
$$\to v_1(d_1)^2 = v_2(d_2)^2$$
### 3. Asas Kontinuitas Kedua

![[pipa3.png#center|350]]
Aliran dalam fluida ideal yang mengalami percabangan maka jumlah debit aliran yang masuk dan keluar percabangan akan selalu sama.
$$Q_{masuk} = Q_{keluar}$$
$$Q_1 = Q_2 + Q_3$$
$$v_1.A_1 = v_2.A_2 + v_3.A_3$$

> [!NOTE] Keterangan
> - $v_1$ : kecepatan aliran 1 ($m/s$)
> - $v_2$ : kecepatan aliran 2 ($m/s$)
> - $A_1$ : 
> - $A_2$ : 
> - $r_1$ : 
> - $r_2$ : 
> - $d_1$ : 
> - $d_2$ : 

## C. Hukum Bernouli

![[bernouli.png#center|200]]
<p align="center">1700-1782</p>
### 1. Hukum 1 Bernoulli Tekanan Statis
Semakin tinggu posisi fluida terhadap titik acuan, maka tekanannya akan semakin rendah. Semakin rendah posisi fluida terhadap titik acuan, maka tekannya akan semakin tinggi.
Belaku untuk fluida yang diam atau bergerak dengan kecepatan tetap.

### 2. Hukum 2 Bernoulli Tekanan Dinamis
Semakin cepat fluida bergerak maka tekanan fluida semakin rendah.
- $v$ semakin tinggi, $P$ semakin rendah.
- $v$ semakin rendah, $P$ semakin tinggi.
#### a. Hukum Bernoullli
Jumlah dari tekanan ($P$), energi kinetik per satuan volume ($\frac{1}{2}\rho v^2$), dan energi potensial per satuan volume ($\rho g h$) adalah selalu tetap pada titik alir sepanjang garis aliran yang sama (kontinu).

> [!WARNING] INGAT!!
> Hukum Bernoulli tidak berlaku pada pipa yang beda aliran (beda sumber).

#### b. Persamaan Dasar Hukum Bernouli
$$$P + \frac{1}{2}\rho v^2 + \rho g h = konstan$$
#### c. Persamaan Hukum Bernoulli 1
Untuk keadaan kecepatan aliran sama dan ketinggi aliran berbeda.

![[pipa4.png#center|350]]
$$P_1 + \rho g h_1 + \frac{1}{2}\rho(v_1)^2 = P_2 + \rho g h_2 + \frac{1}{2}\rho(v_2)^2$$
$$P_1 - P_2 = \rho g h_2 - \rho g h_1$$
$$\Delta P - \rho g (h_2-h_1)$$

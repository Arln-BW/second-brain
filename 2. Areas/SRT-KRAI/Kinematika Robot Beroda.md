---
tags: 
Links: "[[My Areas]]"
---
---
## A. Introduction 
Robot dengan roda omni merupakan salah satu solusi inovatif, contoh seperti perusahaan amazon yang mengimplementasikan untuk robot mobilenya. Robot yang menggunakan roda omni dapat bergerak dalam berbagai arah. Robot yang menggunakan roda omni dalam mengontrolnya perlu memerhatikan arah, struktur geometri, dan analisis koordinat diberbagai suber yang tersedia. Sebagai tambahan, dalam pergerakan robot, arah dan kecepatan putar motor dapat di analisis menggunakan data odometri yang mana data tersebut dapat memprediksi perubahan posisi robot dengan perubahan lingkungannya.

Tujuan dalam jurnal untuk mengimplementasikan model kinematika dan odometri pada robot dengan roda omni, serta mengontrol gerakan robot agar bisa mengikuti lintasan yang telah direncanakan secara akurat menggunakan mikrokontroler sebagai pengendali utama. 

## B. Metode Kinematika pada Robot Menggunakan Omnidirectional Wheel

Kinematika modeling pada robot mempelajari tentang gerakan robot yang berdasar pada analisis struktur geometris terhadap sebuah gerakan yang bersumber dari koordinat sistem tanpa memperdulikan gaya, torsi, atau hal yang dapat memengaruhi gerakan dari luar. Kinematika robot beroda terdapat 2 metode kinematika yaitu kinematika mundur(invers kinematic) dan kinematika maju (fordward kinematic). Dalam perhitungan ini digunakan 4 roda sebagai penggerak dan dipasang 90° terhadap diagonal masing-masing roda.
### 1. Model Kinematika Maju pada Robot Beroda (Forward Kinematics)

Kinematika maju digunakan untuk menghitung kecepatan translasi dan rotasi robot berdasarkan kecepatan putaran masing-masing roda. Dalam kinematika maju, hubungan antara kecepatan sudut roda (input) dan kecepatan linier serta angular dari seluruh robot (output) dihitung menggunakan persamaan kinematika. Untuk menghubungkan kecepatan setiap roda dengan kecepatan robot secara keseluruhan, harus dilakukan pemodelan kecepatan roda dalam tiga komponen : Kecepatan linear arah $x$, kecepatan linear arah $y$ dan kecepatan angular atau rotasi disekitar sumbu $z$ (yaw). Dengan kata lain jika diketahui kecepatan sudut pada setiap roda ($\omega_1,\omega_2,\omega_3,\omega_4$), maka dapat dihitung kecepatan gerak robot di sumbu $x$ dan $y$, serta kecepatan rotasinya di sumbu $z$ (yaw).
- Kecepatan sudut tiap roda dinotasikan dengan : $\omega_w=[\omega_1,\omega_2,\omega_3,\omega_4]^T$
- Kecepatan linear tiap roda dinotasikan dengan : $v_w=[v_1,v_2,v_3,v_4]^T$
Kecepatan roda dapat bernilai positif ketika putaran roda searah jarum jam (clockwise-CW) dan akan bernilai negatif ketiak putaran roda berlawanan arah jarum jam (CCW). 
$$\begin{bmatrix} v_x \\[0.3em] v_y \\[0.3em]\omega_z \end{bmatrix} =
\frac{r}{4}
\begin{bmatrix}
    -1 & 1 & 1 & -1 \\[0.3em]
    1 & 1 & -1 & -1\\[0.3em]
    \frac{1}{L} & \frac{1}{L} & \frac{1}{L} & \frac{1}{L}
\end{bmatrix}
\begin{bmatrix}
	\omega_1 \\[0.3em]
	\omega_2 \\[0.3em]
	\omega_3 \\[0.3em]
	\omega_4 \\[0.3em]
\end{bmatrix}
$$
Sehingga didapatkan :
$$\bigg[ v_x=\frac{r}{4}(\omega_1-\omega_2-\omega_3+\omega_4) \bigg]$$
$$\bigg[ v_y=\frac{r}{4}(\omega_1+\omega_2+\omega_3+\omega_4) \bigg]$$
$$\bigg[ v_x=\frac{r}{4}(\omega_1+\omega_2-\omega_3-\omega_4) \bigg]$$
### 2. Model Kinematika Mundur pada Robot Beroda (Invers Kinematics)

**Kinematika mundur** digunakan untuk menentukan kecepatan sudut masing-masing roda berdasarkan kecepatan translasi dan rotasi yang diinginkan dari robot. Jika kita mengetahui kecepatan translasi robot ($v_x$, $v_y$) dan kecepatan rotasi yaw ($\omega_z$), kita dapat menghitung kecepatan sudut roda ($\omega_1,\omega_2,\omega_3,\omega_4$) yang dibutuhkan untuk mencapai gerakan tersebut. Persamaan kinematika mundur :

$$
\begin{bmatrix}
	\omega_1 \\[0.3em]
	\omega_2 \\[0.3em]
	\omega_3 \\[0.3em]
	\omega_4 \\[0.3em]
\end{bmatrix} = \frac{1}{r}
\begin{bmatrix}
	-1 & 1 & L \\[0.3em]
	 1 & 1 & L \\[0.3em]
	-1 & -1 & L \\[0.3em]
	-1 & -1 & L \\[0.3em]
\end{bmatrix}
\begin{bmatrix}
	v_x \\[0.3em]
	v_y \\[0.3em]
	\omega_z \\[0.3em]
\end{bmatrix}
$$
1. Roda 1 : $v_{w1}=-v_x\sin \alpha_1 + v_y \cos \alpha_1$
2. Roda 2 : $v_{w2}=-v_x\sin(180\degree-\alpha_2)-v_y\cos(180\degree-\alpha_2)$
	$\to v_{w2}=-v_x\sin\alpha_2+v_y\cos\alpha_2$
3. Roda 3 : $v_{w3}= v_x\cos(270\degree-\alpha_2)+v_y\sin(270\degree-\alpha_2)$
	$\to v_{w3}= -v_x\sin\alpha_3+v_y\cos\alpha_3$
4. Roda 4 : $v_{w4}= v_x\sin(360\degree-\alpha_2)+v_y\sin(360\degree-\alpha_2)$
	$\to v_{w4}=-v_x\sin\alpha_4+v_y\cos\alpha_4$

> [!NOTE] Keterangan
> - $v_x$ : kecepatan translasi robot sepanjang sumbu **x** (maju atau mundur).
> - $v_y$ : kecepatan translasi robot sepanjang sumbu **x** (maju atau mundur).
> - $\omega_z$ : kecepatan rotasi robot di sumbu **z** (rotasi yaw).
> - $\omega_1,\omega_2,\omega_3,\omega_4$ : kecepatan sudut masing-masing roda omni.
> - $r$ : radius roda omni
> - $L$ : jarak dari pusat robot ke setiap roda.
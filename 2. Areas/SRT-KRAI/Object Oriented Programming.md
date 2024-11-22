---
tags: 
Links: "[[My Areas]]"
---
---
## Object Oriented Programming

OOP merupakan paradigma pemrograman berbasis objek dan sebuah pendekatan pemrograman yang menggunakan konsep objek sebagai elemen utama dalam membuat program. Setiap objek berupa kelas yang bisa mendefinisikan atribut atau properti. Paradigma oop berfokus pada pengorganisasian program ke dalam objek-objek yang berinteraksi satu sama lain untuk mencapai tujuan tertentu

### Konsep Utama OOP:

1. **Kelas (Class)**: Cetakan atau blueprint untuk menciptakan objek. Di dalam kelas, didefinisikan atribut (data) dan metode (fungsi).
2. **Objek (Object)**: Entitas atau properti nyata yang merupakan instansi dari kelas. Setiap objek dapat memiliki nilai atribut yang berbeda tetapi metode yang sama.
3. **Enkapsulasi (Encapsulation)**: Menyembunyikan detail implementasi dari luar, hanya memperlihatkan bagian yang diperlukan melalui interface (fungsi publik). Ini menjaga keamanan dan konsistensi data.
4. **Pewarisan (Inheritance)**: Kelas dapat mewarisi sifat dan metode dari kelas lain. Ini memungkinkan penggunaan kembali kode dan membangun hubungan antar kelas.
5. **Polimorfisme (Polymorphism)**: Kemampuan untuk menggunakan metode yang sama pada kelas-kelas berbeda. Metode ini dapat memiliki implementasi yang berbeda tergantung pada objek yang memanggilnya.
6. **Abstraksi (Abstraction)**: Penyederhanaan kompleksitas dengan hanya menampilkan elemen penting dari objek tanpa menunjukkan detail internal.

### Penerapan OOP dalam Pemrograman untuk Menyelesaikan Masalah:

OOP sangat bermanfaat untuk menyelesaikan masalah-masalah kompleks dengan cara membaginya menjadi objek-objek kecil yang lebih mudah dikelola. Berikut adalah beberapa penerapan OOP:

1. **Mengelola Kompleksitas**: OOP membantu memecah masalah besar menjadi objek-objek kecil yang independen. Setiap objek memiliki tanggung jawab spesifik yang membuat program lebih modular dan mudah dipelihara. Misalnya, dalam aplikasi sistem manajemen perpustakaan, kita bisa memiliki kelas seperti `Buku`, `Anggota`, dan `Transaksi`. Setiap kelas memiliki atribut dan metode yang terkait dengannya.
    
2. **Penggunaan Kembali Kode (Code Reusability)**: Dengan pewarisan, kelas-kelas baru dapat dibangun dari kelas yang sudah ada. Misalnya, jika kita memiliki kelas `Kendaraan`, kita bisa membuat kelas turunan seperti `Mobil` atau `Motor`, yang mewarisi atribut dan metode dari kelas `Kendaraan` tapi juga memiliki fitur spesifik mereka sendiri.
    
3. **Pemeliharaan yang Mudah**: OOP memudahkan perawatan kode. Jika ada perubahan pada satu objek, perubahan itu tidak mempengaruhi objek lain, karena objek memiliki data dan fungsinya sendiri. Misalnya, dalam aplikasi sistem keuangan, jika ada perubahan dalam perhitungan bunga, kita hanya perlu memperbarui fungsi terkait pada objek yang relevan tanpa memengaruhi seluruh sistem.
    
4. **Enkapsulasi Data**: OOP menjaga keamanan dan integritas data dengan menyembunyikan detail implementasi dan hanya menampilkan interface publik yang dibutuhkan. Hal ini mencegah perubahan langsung terhadap data yang sensitif dari luar kelas.
    
5. **Polimorfisme untuk Fleksibilitas**: Dengan polimorfisme, kita dapat mendefinisikan metode yang sama dalam kelas yang berbeda, sehingga kode bisa lebih fleksibel dan serbaguna. Misalnya, metode `cetak()` dalam kelas `Dokumen` bisa memiliki implementasi berbeda dalam kelas `Laporan` atau `Struk`, tapi dengan cara pemanggilan yang sama.

## Array Introduction

```cpp
#include <iostream>
using namespace std;

int main(int arg, char const *argv[]){
	// membuat array
	int data[5];
	nilai[0] = 10;
	
	// Cara lain
	int value[5] = {1, 2, 3, 4};
	cin.get():
	return 0;
}
```
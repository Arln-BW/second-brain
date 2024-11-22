---
tags:
  - cpp
Links: "[[Programming]]"
---
---
## A. Kompilasi

` g++ -0 <nama_berkas> <nama_programFile> `

- `<nama berkas>` diisi dengan nama berkas hasil kompilasi yang diinginkan.
- `<nama program>` diisi dengan nama berkas C++ yang hendak dikompilasi.

Untuk menjalankan program, hanya ketik `<nama_berkas>` yang digunakan saat kompilasi
## B. Mencetak dengan std::cout
Perintah pertama : 
```c++
std::cout << "Halo, dunia!" << std::endl;
```
### 1. String
- `std::cout` (singkatan dari "_character output_") akan mencetak nilai-nilai yang berada setelahnya.
- Setiap nilai yang ingin dicetak harus didahului dengan **operator** `<<`.
- Terdapat dua nilai yang dicetak:
    - **String** `"Halo, dunia"`, menyatakan teks `Halo, dunia!`.
        - String harus diapit dengan tanda kutip dua (`"`).
    - `std::endl` (singkatan dari "_end of line_"), menandakan akhir dari baris.
        - Mirip dengan Enter pada _keyboard_.
- `;` menandakan akhir dari sebuah perintah.
### 2. Nilai
Mencetak bilangan dan string hanya berbeda saat tanda kutip dua (`"`) digunakan atau tidak.
- Nilai berupa string diapit dengan tanda kutip dua (`"`).
- Nilai berupa bilangan **tidak diapit** dengan tanda kutip dua.

>[!NOTE] Note :
>Pada C++, nilai `"75"` adalah string, sedangkan nilai `75` adalah bilangan (bulat). Jika dicetak, keduanya menghasilkan keluaran yang sama, yakni teks `75`. Akan tetapi, nilai berupa bilangan memungkinkan kita untuk melakukan perhitungan **ekspresi aritmetika**.
## C. Mencetak dengan printf()

```c++
#include <iostream>
using namespace std;

int x;
int main() {
	x = 12;
	printf("Nilai = %d\n", x);
}
```

- Untuk pencetakan, digunakan perintah berikut : `printf("Nilai = %d\n", x)`;
- Untuk mencetak nilai dari variabel, diperlukan simbol sementara yang akan digantikan dengan nilai variabel.
- Simbol sementara untuk variabel bertipe bilangan bulat seperti x adalah `%d`
- Variabel-variabel untuk menggantikan simbol sementara perlu dituliskan sesudah pola cetakan.

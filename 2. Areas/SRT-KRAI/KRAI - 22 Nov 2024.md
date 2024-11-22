---
tags: 
Links: "[[My Areas]]"
---
---
## File esp32.ino
### 1. Include Library
```cpp
#include "SerialTransfer.h"
#include <PS4Controller.h>
```
bisa dicari tahu tentang library yang digunakan, method apa yang dipakai. Gunakan preprocessing untuk melihat struktur dari library [SerialTrasfer.h]() dan [PS$Controller.h]().
### 2. Deklarasi ESP32
menggunakan protokol `SerialTransfer` dengan cara
```cpp
SerialTransfer esp32;
```
### 3. Membuat Object atau Struct
Struct yang dibuat untuk mendeklarasikan komponen yang dibutuhkan untuk pergerakan robot yang akan di terima oleh esp32 dan sinyal dikirimkan melalui controller PS4.
```cpp
struct movement {
	bool up, down, right, left;
	int16_t lx, ly;
} robot;
```
`up`, `down`, `right`, dan `left` merupakan variabel yang berupa boolean yang akan menerima kondisi benar dan salah ketika tombol arrow ditekan atau tidak. `lx` dan `ly` berupa tipe data integer yang memiliki nilai 16 bit. 

`lx` dan `ly` merupakan variabel yang akan menerima sebuah data yang realtime dari controller PS4 berupa analog kiri. `robot` merupakan sebuah tipe data `movement` yang berisi komponen struct yang sudah dideklarasikan membernya.
### 4. void setup()
Pada `void setup()` merpakan berisi program deklarasi yang dibutuhkan untuk menjalankan program yang dibutuhkan selanjutnya. Berisi :
```cpp
void setup(){
  esp32.begin(Serial0);
  Serial0.begin(57600);
  Serial.begin(57600);
  esp32.begin(Serial);
  PS4.begin("c0:49:ef:f8:36:3c");
}
```
- `esp32.begin(serial0)` untuk mendeklarasikan pin serial yang digunakan untuk transfer anatara esp32 dan arduino mega
- `Serial0.begin(57600);` Serial0 yang sebagai tx data diset memiliki baud rate sebesar 57600
- `Serial.begin(57600);` merupakan komunikasi serial pada arduino yang diset pada baud rate 57600
- 
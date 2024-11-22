---
tags: 
Links: "[[My Areas]]"
---
---
Berikut adalah contoh program untuk mengendalikan robot dengan 4 driver motor **BTS7960** yang dikendalikan oleh **kontroller PS4**. Program ini menggerakkan robot dalam sumbu **X** (kanan/kiri) atau **Y** (maju/mundur) sesuai dengan input dari tombol arah pada PS4. Kontroller akan mengirimkan data ke **ESP32**, lalu perintah tersebut dikirim ke **Arduino Mega** melalui komunikasi **UART** dengan menggunakan **library SerialTransfer**.

### 1. **Program untuk ESP32**
ESP32 akan menerima input dari kontroller PS4, lalu mengirimkan perintah (arah gerakan) ke Arduino Mega menggunakan komunikasi serial.

```cpp
#include <PS4Controller.h>
#include <SerialTransfer.h>

SerialTransfer myTransfer;

void setup() {
  Serial.begin(115200);
  Serial2.begin(9600, SERIAL_8N1, 16, 17);  // UART komunikasi dengan Arduino Mega (TX=17, RX=16)
  myTransfer.begin(Serial2);

  PS4.begin("e8:6b:ea:df:45:de");  // Ganti dengan alamat MAC dari ESP32 jika diperlukan
  PS4.attach(onConnect);
}

void loop() {
  if (PS4.isConnected()) {
    uint8_t movement = 0;

    if (PS4.Up()) {
      movement = 1; // Maju (sumbu Y+)
    } else if (PS4.Down()) {
      movement = 2; // Mundur (sumbu Y-)
    } else if (PS4.Right()) {
      movement = 3; // Ke kanan (sumbu X+)
    } else if (PS4.Left()) {
      movement = 4; // Ke kiri (sumbu X-)
    }

    // Kirimkan data gerakan ke Arduino Mega
    if (movement > 0) {
      myTransfer.txObj(movement);
      myTransfer.sendData(sizeof(movement));

      delay(1000);
    }
  }
}

void onConnect() {
  Serial.println("terhubung");
}
```

### 2. **Program untuk Arduino Mega**
Arduino Mega akan menerima perintah dari ESP32 dan mengendalikan motor sesuai dengan data yang diterima.

```cpp
#include <SerialTransfer.h>

SerialTransfer myTransfer;

const int frontRight = 5;
const int frontLeft = 6;
const int backRight = 9;
const int backLeft = 8;

const int sfrontRight = 36;
const int sfrontLeft = 34;
const int sbackRight = 32;
const int sbackLeft = 30;

void setup() {
  Serial.begin(115200);  // Untuk debugging
  Serial1.begin(9600);   // UART komunikasi dengan ESP32
  myTransfer.begin(Serial1);

  // Atur pin motor sebagai output
  pinMode(frontRight, OUTPUT);
  pinMode(frontLeft, OUTPUT);
  pinMode(backRight, OUTPUT);
  pinMode(backLeft,OUTPUT);

  pinMode(sfrontRight, OUTPUT);
  pinMode(sfrontLeft, OUTPUT);
  pinMode(sbackRight, OUTPUT);
  pinMode(sbackLeft, OUTPUT);
}

void loop() {
  if (myTransfer.available()) {
    uint8_t movement;
    myTransfer.rxObj(movement);

    // Kontrol gerakan berdasarkan data yang diterima
    switch (movement) {
      case 1: // Maju
        moveForward();
        break;
      case 2: // Mundur
        moveBackward();
        break;
      case 3: // Kanan
        moveRight();
        break;
      case 4: // Kiri
        moveLeft();
        break;
    }
  }
}

void moveForward() {
  controlMotor(motor1_pwm, motor1_dir, 255);  // Maju
  controlMotor(motor2_pwm, motor2_dir, 255);  // Maju
  controlMotor(motor3_pwm, motor3_dir, 255);  // Maju
  controlMotor(motor4_pwm, motor4_dir, 255);  // Maju
}

void moveBackward() {
  controlMotor(motor1_pwm, motor1_dir, -255); // Mundur
  controlMotor(motor2_pwm, motor2_dir, -255); // Mundur
  controlMotor(motor3_pwm, motor3_dir, -255); // Mundur
  controlMotor(motor4_pwm, motor4_dir, -255); // Mundur
}

void moveRight() {
  controlMotor(frontRight, motor1_dir, 255);  // Kanan
  controlMotor(motor2_pwm, motor2_dir, -255); // Kanan
  controlMotor(motor3_pwm, motor3_dir, -255); // Kanan
  controlMotor(motor4_pwm, motor4_dir, 255);  // Kanan
}

void moveLeft() {
  controlMotor(motor1_pwm, motor1_dir, -255); // Kiri
  controlMotor(motor2_pwm, motor2_dir, 255);  // Kiri
  controlMotor(motor3_pwm, motor3_dir, 255);  // Kiri
  controlMotor(motor4_pwm, motor4_dir, -255); // Kiri
}

void controlMotor(int pwmPin, int dirPin, int speed) {
  if (speed >= 0) {
    digitalWrite(dirPin, HIGH);
    analogWrite(pwmPin, speed);
  } else {
    digitalWrite(dirPin, LOW);
    analogWrite(pwmPin, -speed);
  }
}
```

### Penjelasan:

1. **ESP32**:
   - Menerima input dari **kontroller PS4** melalui Bluetooth.
   - Menekan tombol **Up** untuk maju, **Down** untuk mundur, **Right** untuk bergerak ke kanan, dan **Left** untuk bergerak ke kiri.
   - Data arah gerakan dikirimkan ke Arduino Mega melalui UART dengan bantuan **library SerialTransfer**.

2. **Arduino Mega**:
   - Menerima data gerakan (arah) dari ESP32 dan mengontrol keempat motor roda omni berdasarkan data yang diterima.
   - Fungsi `moveForward()`, `moveBackward()`, `moveRight()`, dan `moveLeft()` mengatur kecepatan dan arah motor sesuai dengan perintah.

3. **Driver Motor BTS7960**:
   - Pin PWM dan arah dikontrol dari Arduino Mega untuk menjalankan pergerakan robot.

Program ini dapat kamu modifikasi lebih lanjut jika perlu, misalnya menambahkan pengaturan kecepatan motor atau kondisi tambahan sesuai dengan kebutuhan sistem robotmu.


---

Berikut adalah contoh program yang bisa kamu gunakan untuk mengendalikan robot dengan 4 driver motor **BTS7960** yang dikendalikan oleh **kontroller PS4**, dengan **ESP32** untuk menerima perintah dan mengirimkannya ke **Arduino Mega** melalui komunikasi **Serial UART** menggunakan **library SerialTransfer**.

### 1. **Program untuk ESP32**
ESP32 akan menerima input dari kontroller PS4, lalu mengirimkan perintah tersebut ke Arduino Mega menggunakan komunikasi serial.

```cpp
#include <PS4Controller.h>
#include <SerialTransfer.h>

SerialTransfer myTransfer;

void setup() {
  Serial.begin(115200);
  Serial2.begin(9600, SERIAL_8N1, 16, 17);  // UART untuk komunikasi dengan Arduino Mega (TX=17, RX=16)
  myTransfer.begin(Serial2);

  PS4.begin("xx:xx:xx:xx:xx:xx");  // Ganti dengan alamat MAC dari ESP32 jika perlu
  PS4.attach(onConnect);
}

void loop() {
  if (PS4.isConnected()) {
    int leftX = PS4.LStickX();   
    int leftY = PS4.LStickY();   
    int rightX = PS4.RStickX(); 
    
    // data yang dikirim ke arduino
    uint8_t sendData[3] = {leftX, leftY, rightX};
    myTransfer.txObj(sendData, sizeof(sendData));
    myTransfer.sendData(sizeof(sendData));

    delay(1000); 
  }
}

void onConnect() {
  Serial.println("Kontroller PS4 terhubung!");
}
```

### 2. **Program untuk Arduino Mega**
Arduino Mega akan menerima perintah dari ESP32 dan mengendalikan motor sesuai dengan data yang diterima.

```cpp
#include <SerialTransfer.h>

SerialTransfer myTransfer;

const int motor1_pwm = 3;   // Pin PWM motor 1
const int motor1_dir = 4;   // Pin arah motor 1
const int motor2_pwm = 5;   // Pin PWM motor 2
const int motor2_dir = 6;   // Pin arah motor 2
const int motor3_pwm = 9;   // Pin PWM motor 3
const int motor3_dir = 10;  // Pin arah motor 3
const int motor4_pwm = 11;  // Pin PWM motor 4
const int motor4_dir = 12;  // Pin arah motor 4

void setup() {
  Serial.begin(115200);
  Serial1.begin(9600);
  myTransfer.begin(Serial1);

  // Atur pin motor sebagai output
  pinMode(motor1_pwm, OUTPUT);
  pinMode(motor1_dir, OUTPUT);
  pinMode(motor2_pwm, OUTPUT);
  pinMode(motor2_dir, OUTPUT);
  pinMode(motor3_pwm, OUTPUT);
  pinMode(motor3_dir, OUTPUT);
  pinMode(motor4_pwm, OUTPUT);
  pinMode(motor4_dir, OUTPUT);
}

void loop() {
  if (myTransfer.available()) {
    uint8_t receivedData[3];
    myTransfer.rxObj(receivedData, sizeof(receivedData));

    int leftX = receivedData[0];
    int leftY = receivedData[1];
    int rightX = receivedData[2];

    // Algoritma kontrol untuk roda omni
    int motor1_speed = leftY + leftX + rightX;
    int motor2_speed = leftY - leftX - rightX;
    int motor3_speed = leftY - leftX + rightX;
    int motor4_speed = leftY + leftX - rightX;

    // Fungsi kontrol motor
    controlMotor(motor1_pwm, motor1_dir, motor1_speed);
    controlMotor(motor2_pwm, motor2_dir, motor2_speed);
    controlMotor(motor3_pwm, motor3_dir, motor3_speed);
    controlMotor(motor4_pwm, motor4_dir, motor4_speed);
  }
}

void controlMotor(int pwmPin, int dirPin, int speed) {
  if (speed >= 0) {
    digitalWrite(dirPin, HIGH);
    analogWrite(pwmPin, speed);
  } else {
    digitalWrite(dirPin, LOW);
    analogWrite(pwmPin, -speed);
  }
}
```

### Penjelasan:

1. **ESP32**:
   - Terhubung dengan kontroller PS4 melalui Bluetooth.
   - Data pergerakan dari joystick kiri (`leftX`, `leftY`) dan kanan (`rightX`) dikirim ke Arduino Mega melalui serial (UART) menggunakan **library SerialTransfer**.

2. **Arduino Mega**:
   - Menerima data dari ESP32 dan menggunakan algoritma untuk mengontrol 4 motor roda omni.
   - Algoritma kontrol motor sederhana berdasarkan arah joystick.

3. **Driver Motor BTS7960**:
   - Pin PWM dan pin arah dikendalikan dari Arduino Mega berdasarkan input dari joystick.

Program ini adalah contoh dasar. Kamu dapat memodifikasi sesuai kebutuhan seperti mengatur kecepatan maksimum, kalibrasi joystick, atau menambah logika kontrol lainnya.
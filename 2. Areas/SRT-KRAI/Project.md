---
tags: 
Links: "[[My Areas]]"
---
---
# KRAI-Programmer Project
## Serial Communication ESP32 & Arduino Mega
Serial komunikasi berfungsi untuk menjalankan sebuah program dan ketika ada keperluan untuk melakukan debugging akan mudah untuk dilakukan. Pada pada komunikasi antar mikrokontroller ini, ada input dari controller untuk mengendalikan 4 buah roda omni yang akan menggerakkan robot. Masukkan dari Controller berupa tombol arrow untuk bergerak maju, mundur, kanan dan kiri. Programnya sebagai berikut
### 1. Program untuk ESP32

```cpp
#include "SerialTransfer.h"
#include <PS4Controller.h>
SerialTransfer esp32; 

struct movement {
  bool up;
  bool down;
  bool right;
  bool left;
} robot;  

void setup(){
  esp32.begin(Serial0);
  Serial0.begin(57600);
  Serial.begin(57600);
  esp32.begin(Serial);
  PS4.begin("c0:49:ef:f8:36:3c");
} 

void loop(){
  if (PS4.isConnected()){
    int32_t sendSize = 0;
    sendSize = esp32.txObj(robot, sendSize);
    esp32.sendData(sendSize);
    robot.up = PS4.Up();
    robot.down = PS4.Down();
    robot.right = PS4.Right();
    robot.left = PS4.Left();
  }
}
```
### 2. Program untuk Arduino

```cpp
#include "SerialTransfer.h"

SerialTransfer arduino;

const int frontRight = 5;
const int frontLeft = 6;
const int backRight = 9;
const int backLeft = 8;

const int sfrontRight = 36;
const int sfrontLeft = 34;
const int sbackRight = 32;
const int sbackLeft = 30;

struct movement{
  bool up;
  bool down;
  bool right;
  bool left;
} robot;

void setup(){
  arduino.begin(Serial3);
  Serial.begin(57600);
  Serial3.begin(57600);

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
  if(arduino.available()){
    int32_t recSize = 0;
    recSize = arduino.rxObj(robot, recSize);

    if (robot.up == 1) moveForward();
    else if (robot.down == 1) moveBackward();
    else if (robot.right == 1) moveRight();
    else if (robot.left == 1) moveLeft();
    else stop();
  }
}

  

void moveForward(){
  analogWrite(frontRight, 100);
  digitalWrite(sfrontRight, HIGH);

  analogWrite(frontLeft, 100);
  digitalWrite(sfrontLeft, LOW);

  analogWrite(backRight, 100);
  digitalWrite(sbackRight, HIGH);
  
  analogWrite(backLeft, 100);
  digitalWrite(sbackLeft, LOW);
}

  

void moveBackward(){
  analogWrite(frontRight, 100);
  digitalWrite(sfrontRight, LOW);

  analogWrite(frontLeft, 100);
  digitalWrite(sfrontLeft, HIGH);

  analogWrite(backRight, 100);
  digitalWrite(sbackRight, LOW);

  analogWrite(backLeft, 100);
  digitalWrite(sbackLeft, HIGH);
}

void moveRight(){
  analogWrite(frontRight, 100);
  digitalWrite(sfrontRight, LOW); 

  analogWrite(frontLeft, 100);
  digitalWrite(sfrontLeft, LOW); 

  analogWrite(backRight, 100);
  digitalWrite(sbackRight, HIGH);

  analogWrite(backLeft, 100);
  digitalWrite(sbackLeft, HIGH);

}

void moveLeft(){
  analogWrite(frontRight, 100);
  digitalWrite(sfrontRight, HIGH);

  analogWrite(frontLeft, 100);
  digitalWrite(sfrontLeft, HIGH);

  analogWrite(backRight, 100);
  digitalWrite(sbackRight, LOW);

  analogWrite(backLeft, 100);
  digitalWrite(sbackLeft, LOW);
}

  

void stop(){
  analogWrite(frontRight, 0);
  digitalWrite(sfrontRight, HIGH);

  analogWrite(frontLeft, 0);
  digitalWrite(sfrontLeft, HIGH);

  analogWrite(backRight, 0);
  digitalWrite(sbackRight, LOW);
  
  analogWrite(backLeft, 0);
  digitalWrite(sbackLeft, LOW);
}
```

---
## Pergerakan Robot dengan Kinematika Balik (Inverse Kinematic) dan Penerapan Konsep OOP

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
1. Roda 1 : $$v_{w1}=-v_x\sin \alpha_1 + v_y \cos \alpha_1$$
2. Roda 2 : $$v_{w2}=-v_x\sin(180\degree-\alpha_2)-v_y\cos(180\degree-\alpha_2)$$$$\implies v_{w2}=-v_x\sin\alpha_2+v_y\cos\alpha_2$$
3. Roda 3 : $$v_{w3}= v_x\cos(270\degree-\alpha_2)+v_y\sin(270\degree-\alpha_2)$$$$\implies v_{w3}= -v_x\sin\alpha_3+v_y\cos\alpha_3$$
4. Roda 4 : $$v_{w4}= v_x\sin(360\degree-\alpha_2)+v_y\sin(360\degree-\alpha_2)$$$$\implies v_{w4}=-v_x\sin\alpha_4+v_y\cos\alpha_4$$
> [!NOTE] Keterangan
> - $v_x$ : kecepatan translasi robot sepanjang sumbu **x** (maju atau mundur).
> - $v_y$ : kecepatan translasi robot sepanjang sumbu **x** (maju atau mundur).
> - $\omega_z$ : kecepatan rotasi robot di sumbu **z** (rotasi yaw).
> - $\omega_1,\omega_2,\omega_3,\omega_4$ : kecepatan sudut masing-masing roda omni.
> - $r$ : radius roda omni
> - $L$ : jarak dari pusat robot ke setiap roda.

### 1. Program untuk ESP32

```cpp
#include "SerialTransfer.h"
#include <PS4Controller.h>
SerialTransfer esp32; 

struct movement {
  bool up;
  bool down;
  bool right;
  bool left;
  int32_t lx;
  int32_t ly;
} robot;  

void setup(){
  esp32.begin(Serial0);
  Serial0.begin(57600);
  Serial.begin(57600);
  esp32.begin(Serial);
  PS4.begin("c0:49:ef:f8:36:3c");
} 

void loop(){
  if (PS4.isConnected()){
    int32_t sendSize = 0;
    sendSize = esp32.txObj(robot, sendSize);
    esp32.sendData(sendSize);
    robot.up = PS4.Up();
    robot.down = PS4.Down();
    robot.right = PS4.Right();
    robot.left = PS4.Left();
    robot.lx = PS4.LStickX();
    robot.ly = PS4.LStickY();
  }
}
```

### 2. Program untuk Arduino
#### a. Program Utama

```cpp
#include "motor.h"
#include "rangkaBawah.h"
#include "inversKinematic.h"
#include "SerialTransfer.h"

SerialTransfer arduino;

struct movement{
  bool up;
  bool down;
  bool right;
  bool left;
  int32_t lx;
  int32_t ly;
} robot;

int pwm = 150;
float v_w1, v_w2, v_w3, v_w4;

double rad1 = (3.14/180)*45;
double rad2 = (3.14/180)*135;
double rad3 = (3.14/180)*225;
double rad4 = (3.14/180)*315;

int x; // nilainya dapat dari serial communication yang gak tau gimana caranya:)
int y;// nilainya dapat dari serial communication yang gak tau gimana caranya:)
float alpha;
float v_x, v_y;

Motor motorFR(5, 36);
Motor motorFL(6, 34);
Motor motorBR(9, 32);
Motor motorBL(8, 30);

RangkaBawah RB(motorFR, motorFL, motorBR, motorBL);
Kinematic kinematic;

void setup() {
  arduino.begin(Serial3);
  Serial.begin(57600);
  Serial3.begin(57600);
  RB.setupPin();
} 

void loop() {
  if(arduino.available()){
    int32_t recSize = 0;
    recSize = arduino.rxObj(robot, recSize);
    
    if (abs(robot.ly) < 5 && abs(robot.lx) < 5) {
      v_x = 0;
      v_y = 0;
    } else {
      alpha = atan2(robot.ly, robot.lx);
      v_x = pwm*cos(alpha);
      v_y = pwm*sin(alpha);
    } 

    if (robot.up == 1) RB.maju();
    else if (robot.down == 1) RB.mundur();
    else if (robot.right == 1) RB.kanan();
    else if (robot.left == 1) RB.kiri();
    else RB.stop();

    v_w1 = kinematic.invKinematic(rad1, v_x, v_y);
    v_w2 = kinematic.invKinematic(rad2, v_x, v_y);
    v_w3 = kinematic.invKinematic(rad3, v_x, v_y);
    v_w4 = kinematic.invKinematic(rad4, v_x, v_y);
  }
  RB.moveRobot(v_w1, v_w2, v_w3, v_w4);
}
```

#### b. Program rangkaBawah.cpp

```cpp
#include "Arduino.h"
#include "rangkaBawah.h"

RangkaBawah::RangkaBawah(Motor motorFR, Motor motorFL, Motor motorBR, Motor motorBL){
  this->motorFR = motorFR;
  this->motorFL = motorFL;
  this->motorBR = motorBR;
  this->motorBL = motorBL;
}

void RangkaBawah::setupPin(){
  motorFR.setupPin();
  motorFL.setupPin();
  motorBR.setupPin();
  motorBL.setupPin();
} 

void RangkaBawah::moveRobot(float v_w1, float v_w2, float v_w3, float v_w4){
  if (v_w1 > 0) {
     motorFR.CW(v_w1);
   }else if (v_w1 < 0) {
     motorFR.CCW(v_w1*-1);
   }else {
     motorFR.stop();
  }

  if (v_w2 > 0) {
     motorFL.CW(v_w2);
   }else if (v_w2 < 0) {
     motorFL.CCW(v_w2*-1);
   }else {
     motorFL.stop();
  }
  
  if (v_w3 > 0) {
     motorBL.CW(v_w3);
   }else if (v_w3 < 0) {
     motorBL.CCW(v_w3*-1);
   }else {
     motorBL.stop();
  }

  if (v_w4 > 0) {
     motorBR.CW(v_w4);
   }else if (v_w4 < 0) {
     motorBR.CCW(v_w4*-1);
   }else {
     motorBR.stop();
  }
}

void RangkaBawah::maju(){
  motorFR.CW(150);
  motorFL.CCW(150);
  motorBR.CW(150);
  motorBL.CCW(150);
}

void RangkaBawah::mundur(){
  motorFR.CCW(150);
  motorFL.CW(150);
  motorBR.CCW(150);
  motorBL.CW(150);
}

void RangkaBawah::kanan(){
  motorFR.CCW(150);
  motorFL.CCW(150);
  motorBR.CW(150);
  motorBL.CW(150);
}

void RangkaBawah::kiri(){
  motorFR.CW(150);
  motorFL.CW(150);
  motorBR.CCW(150);
  motorBL.CCW(150);
}

void RangkaBawah::stop(){
  motorFR.CW(0);
  motorFL.CW(0);
  motorBL.CCW(0);
  motorBR.CCW(0);
}
```
#### c. Program rangkaBawah.h

```cpp
#include "motor.h"
#ifndef RB_H
#define RB_H

class RangkaBawah{
  private:
    Motor motorFR;
    Motor motorFL;
    Motor motorBR;
    Motor motorBL;
  public:
    RangkaBawah(
      Motor motorFR,
      Motor motorFL,
      Motor motorBR,
      Motor motorBL
    );

    void moveRobot(float v_w1, float v_w2, float v_w3, float v_w4);
    void setupPin();
    void maju();
    void mundur();
    void kanan();
    void kiri();
    void stop();
};
#endif
```
#### d. Program motor.cpp

```cpp
#include "Arduino.h"

#include "motor.h"

Motor::Motor(){};

void Motor::setupPin(){
  pinMode(this->pwmPin, OUTPUT);
  pinMode(this->selPin, OUTPUT);
};

Motor::Motor(int pwmPin, int selPin){
  this->pwmPin = pwmPin;
  this->selPin = selPin;
};

void Motor::CW(int pwm){
  analogWrite(this->pwmPin, pwm);
  digitalWrite(this->selPin, HIGH);
};

void Motor::CCW(int pwm){
  analogWrite(this->pwmPin, pwm);
  digitalWrite(this->selPin, LOW);
};

void Motor::stop(){
  analogWrite(this->pwmPin, 0);
  digitalWrite(this->selPin, LOW);
}
```
#### e. Program motor.h

```cpp
#ifndef MOTOR_H
#define MOTOR_H
class Motor{
  private:
    int pwmPin;
    int selPin;
  public:
    Motor();
    Motor(int pwmPin, int selPin);
    void CW(int pwm);
    void CCW(int pwm);
    void stop();
    void setupPin();
};
#endif
```
#### f. Program inversKinematic.cpp

```cpp
#include "Arduino.h"
#include "invKinematic.h"
#include "motor.h"

Kinematic::Kinematic(){}
```
#### g. Program inversKinematic.h

```cpp
#include <math.h>
#ifndef KINEMATIC_H
#define KINEMATIC_H

class Kinematic{
  private:
    float alpha, v_x, v_y;
  public:
    Kinematic();
    float invKinematic (float alpha, float v_x, float v_y) {
      return ((-sin(alpha)*v_x) + (cos(alpha)*v_y));
    }
};
#endif
```
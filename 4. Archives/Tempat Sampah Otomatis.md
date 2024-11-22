---
Status:
  - 🟨
tags:
  - project
Links: "[[My Projects]]"
Deadline: 2024-07-14
Area:
---
___
## Tempat Sampah Otomatis Arduino
Tempat sampah yang dimodifikasi menggunakan mikrokontroller berupa arduino uno r3. Arduino diprogram lau dihubungkan menggunakan sensor sebagai pembaca gerakan *Movement* dan dihubungkan juga menggunakan servo sebagai penggerak tutup sampah yang akan dibuat
## Script
### Alat dan bahan yang digunakan
1. Arduino uno r3
2. Sensor HCSR04
3. Mini Servo
4. Kabel Jumper : 6 buah female-male
5. breadboard
6. baterai sebagai power
### Cara Merakit
#### 1. Servo
Kabel oranye -> data (pin 8)
kabel merah -> vcc (5v)
kabel coklat -> negatif
#### 2. Sensor HCSR04
GND -> Kutub Negatif
Echo -> Pin 12
Trig -> Pin 11
VCC -> Kutub Positif
### Program
```cpp
#include <Servo.h>
Servo servo;
int angle = 10;
// defines pins numbers
const int trigPin = 12;
const int echoPin = 11;
// defines variables
long duration;
int distance;
void setup() {
  servo.attach(8);
  servo.write(angle);
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
Serial.begin(9600); // Starts the serial communication
}
void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);
// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);
// Calculating the distance
distance= duration*0.034/2;
// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay(10);

if(distance<100)
{
  servo.write(180);
  delay(4000);
  }
  else
  {
    servo.write(0);
    }
}

```
## References
- [Video](https://youtu.be/aqAUIhVwF6o?si=l7OmYentSTES0tQY)
- [Script](https://docs.google.com/document/d/1b3uPX1HMo47OKhpQixces_KHGnt-RqbnJYF6QoV-15A/edit?usp=drive_link)
- [Circuit Diagram](https://drive.google.com/file/d/1aA1xOKmvIXDPtzQcs_FYtXcarjm5bvKu/view?usp=drive_link)

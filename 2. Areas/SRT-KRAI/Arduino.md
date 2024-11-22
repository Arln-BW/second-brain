---
tags: 
Links: "[[My Areas]]"
---
---
#arduino
## 1. digitalRead

```cpp
//digitalRead

const int pushButton = 3;
const int led = 4;
boolean result;

void setup(){
	Serial.begin(9600);
	pinMode(pushButton, INPUT);
}

void loop(){
	result = digitalRead(pushButton);
	// Serial.println(digitalRead(pushButton));
	if (result == 1) digitalWrite(led, HIGHT);
	else digitalWrite(led, LOW);
	
	delay(1000);
}
```

## 2. Servo & Potentiometer

```cpp
#include <Servo.h>
Servo gerak;
int sensor;
void setup() {
  // put your setup code here, to run once:
  gerak.attach(11);
}

void loop() {
  // put your main code here, to run repeatedly:
  sensor = analogRead(A0);
  int nilai = analogRead(0);
  nilai = map(sensor, 0, 1023, 0, 255);
  gerak.write(nilai);
}

  

// =================================================

// Servo move; 

// int potentiometer = 11;
// int potPin = A0;
// int potValue;
// int servoAngle;

// void setup(){
//   move.attach(11);
//   Serial.begin(9600);
// }

// void loop(){
//   potValue = analogRead(potPin);
//   servoAngle = map(potentiometer, 0, 1023, 0, 255);
//   move.write(servoAngle);
// }
```

## 3. Sensor Ultrasonic

```cpp
const int trigPin = 12;
const int echoPin = 11;

void setup(){
	Serial.begin(9600);
	pinMode(trigPin, OUTPUT);
	pinMode(echoPin, INPUT);
}

void loop(){
	digitalWrite(trigPin, LOW);
	delayMicroseconds(2);
	digitalWrite(trigPin, HIGH);
	delayMicroseconds(10);
	digitalWrite(trigPin, LOW);
	
	long duration = pulseIn(echoPin, HIGH);
	int distance = duration * 0.034/2;
	Serial.print("Jarak: ");
	Serial.print(distance);
	Serial.println(" cm");
	delay(100);
}
```

## 4. Controller

```cpp
#include <PsxControllerBitBang.h>
#include <PsxControllerHwSpi.h>
#include <PsxNewLib.h>
#include <DigitalIO.h>

#include <PS4Controller.h>
#include <ps4.h>
#include <ps4_int.h>
  

const byte PIN_PS2_ATT = 10; // Attention pin
PsxControlledHwSpi<PIN_PS2_ATT> psx;
bool connected = false;
byte LX, LY, RX, RY;
unsigned long prev;
  
void setup() {
	// put your setup code here, to run once:
	Serial.begin(115200);
}  

void loop() {
// put your main code here, to run repeatedly:
	if(millis()-prev >= 25){
		if(!connected) config();
		else{
			if(!psx.read()) Serial.println("Disconnected"); connected = false;
			else readController();
		}
		prev = millis();
	}
}

// Program untuk setup konektor joystick

void readController(){
	psx.getLeftAnalog(LX, LY);
	psx.getRightAnalog(RX, RY);
}
```
🔵 Bluetooth LED Control using Arduino UNO & HC-05
Overview

This project allows you to control three LEDs wirelessly using an HC-05 Bluetooth module and an Arduino UNO.
You can send characters (a–f) from your smartphone via a Bluetooth terminal app to toggle LEDs ON and OFF.

🧠 Working Principle

The Arduino listens for serial data from the HC-05 Bluetooth module through the UART interface.
When specific characters are received, it turns the corresponding LED ON or OFF.

Command	Action
a	Turn ON LED on pin 13
b	Turn OFF LED on pin 13
c	Turn ON LED on pin 12
d	Turn OFF LED on pin 12
e	Turn ON LED on pin 11
f	Turn OFF LED on pin 11
🧩 Components Required

Arduino UNO

HC-05 Bluetooth module

3 × LEDs

3 × 220Ω resistors

Jumper wires

Breadboard

Android smartphone with Bluetooth Terminal App (e.g., Bluetooth Terminal HC-05)

⚙️ Circuit Connections
HC-05 Pin	Arduino Pin	Description
VCC	5V	Power
GND	GND	Ground
TXD	Pin 0 (RX)	Bluetooth → Arduino
RXD	Pin 1 (TX)	Arduino → Bluetooth
LED	Arduino Pin
LED 1	13
LED 2	12
LED 3	11

Note: Remove HC-05 TX/RX pins while uploading the code to Arduino.

💻 Arduino Code
```c
void setup()
{
  Serial.begin(9600);
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(11, OUTPUT);
}

unsigned char data;

void loop()
{
  if (Serial.available()) {
    data = Serial.read();
    if (data == 'a') digitalWrite(13, HIGH);
    if (data == 'b') digitalWrite(13, LOW);
    if (data == 'c') digitalWrite(12, HIGH);
    if (data == 'd') digitalWrite(12, LOW);
    if (data == 'e') digitalWrite(11, HIGH);
    if (data == 'f') digitalWrite(11, LOW);
  }
}
```
📱 How to Use

Upload the code to your Arduino UNO.

Connect the HC-05 module as per the circuit.

Pair your phone with HC-05 (default password: 1234 or 0000).

Open any Bluetooth Terminal app.

Send characters a–f to control LEDs.

🚀 Future Enhancements

Control relays or motors instead of LEDs.

Build a custom Android app using MIT App Inventor.

Integrate voice control via Google Assistant or Alexa.

Use an ESP32 for Wi-Fi + Bluetooth control.

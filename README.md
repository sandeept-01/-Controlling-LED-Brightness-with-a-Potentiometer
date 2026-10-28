# 💡 Potentiometer-Controlled LED Brightness (Arduino Uno)

A simple analog input project built with an Arduino Uno, a potentiometer, and an LED.  
Turning the potentiometer knob smoothly increases or decreases the LED's brightness using PWM, instead of just switching it on and off.

---

## 🔗 Project Links

| Resource | Link |
|---|---|
| 📄 **Full Documentation (Google Docs)** | [Click here to view](https://docs.google.com/document/d/1HQApoagWFLsGaXBFklyWkWVeLKDE0tXIdVVNjc7lYAs/edit?usp=sharing) |
| 🔌 **Simulation (Tinkercad)** | [Open the simulation](https://www.tinkercad.com/things/dOAy2SESIs0-mightybruticus?sharecode=orVdYBrijigBYwX2xLbXogjrXsEnT2UGf1Ox23PpBME) |

---

## 📋 About

The Google Doc above contains the complete write-up:
- Components list and wiring table
- Step-by-step build instructions
- Explanation of how PWM is used to control LED brightness
- Full code breakdown and working explanation
- Output screenshots from the simulation

---

## 🧰 Components

| Component | Quantity |
|---|---|
| Arduino Uno | 1 |
| Potentiometer (1kΩ Rotary) | 1 |
| LED (Standard) | 1 |
| Current-Limiting Resistor (220Ω / 330Ω) | 1 |
| Breadboard | 1 |
| Jumper Wires | As required |

---

## 🔌 Circuit Wiring

### Potentiometer Setup
- **Pin 1** (left pin) → Arduino **5V**
- **Pin 3** (right pin) → Arduino **GND**
- **Pin 2** (middle wiper pin) → Arduino **A0** (Analog Input)

### LED Circuit Setup
- **Anode** (longer leg) → 220Ω Resistor → Arduino pin **~9** (PWM-enabled)
- **Cathode** (shorter leg) → **GND** rail

---

## 💻 Code

```cpp
const int potPin = A0;
const int ledPin = 9;

void setup() {
  pinMode(ledPin, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  int potValue = analogRead(potPin);
  int brightness = map(potValue, 0, 1023, 0, 255);
  analogWrite(ledPin, brightness);

  Serial.print("Potentiometer: ");
  Serial.print(potValue);
  Serial.print(" | LED Brightness: ");
  Serial.println(brightness);

  delay(10);
}

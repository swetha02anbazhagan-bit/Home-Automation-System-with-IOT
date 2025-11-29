# Home-Automation-System-wit-IOT

# AIM: 
  To make a Lamp at home (230 V AC) On / Off using ESP8266, IFTT Google Assistance and Blynk IoT mobile application.          
           
# COMPONENTS REQUIRED:
PC with Internet connection
Micro USB cable
Wifi connection for ESP8266 (Use any mobile hotspot or Router)
	ESP8266 Board
	Mobile Phone with Blynk App installed
            IFTT for Google Voice Assistance
	9 W Bulb and Relay control
Arduino software 
Jumper Wires

## Theory: 
This experiment demonstrates a basic home automation system using an Arduino UNO that integrates sensors, user input, and output devices. An LDR is used to detect ambient light based on its property of varying resistance with light intensity. A TMP36 temperature sensor provides an analog voltage proportional to temperature, which the Arduino reads using its ADC. A push button allows manual user control, while a buzzer and LED act as output indicators. A 16×2 LCD display is interfaced in 4-bit mode to show real-time light and temperature readings. The Arduino continuously processes the sensor values and updates the display, while the button triggers LED and buzzer activation. The experiment highlights the fundamentals of sensing, analog-to-digital conversion, display interfacing, and automation control—representing a simplified model of smart-home technology.

# PROCEDURE:

# ✅ **PROCEDURE FOR HOME AUTOMATION CIRCUIT IN TINKERCAD**

## **1. Components Required**

* Arduino UNO
* Breadboard
* LCD 16×2 (with pins, not I2C)
* Potentiometer (for LCD contrast)
* LDR (Light Dependent Resistor)
* Temperature Sensor (TMP36)
* Buzzer
* Push Button
* LED
* Jumper wires
* 220Ω resistors

---

# ✅ **2. Circuit Assembly Steps**

## **A. Set Up the LCD (16×2)**

1. Place the **LCD** on the breadboard.
2. Make the following connections:

| LCD Pin  | Connect To                                     |
| -------- | ---------------------------------------------- |
| VSS      | GND                                            |
| VDD      | 5V                                             |
| VO       | Middle pin of potentiometer (contrast control) |
| RS       | Arduino Digital Pin 7                          |
| RW       | GND                                            |
| E        | Arduino Digital Pin 8                          |
| D4       | Arduino Digital Pin 9                          |
| D5       | Arduino Digital Pin 10                         |
| D6       | Arduino Digital Pin 11                         |
| D7       | Arduino Digital Pin 12                         |
| A (LED+) | 5V through 220Ω resistor                       |
| K (LED–) | GND                                            |

3. Connect potentiometer:

   * Left pin → 5V
   * Right pin → GND
   * Middle pin → LCD VO

---

## **B. Connect the LDR (Light Sensor)**

1. Place the **LDR** on the breadboard.
2. One leg → **5V**
3. Other leg → **A0**
4. Also connect a **10k resistor** from that leg to **GND**
   (This forms a voltage divider.)

---

## **C. Connect Temperature Sensor (TMP36)**

1. Flat side facing you:

   * Left pin → **5V**
   * Middle pin → **A1**
   * Right pin → **GND**

---

## **D. Connect the Button**

1. Place push button across the breadboard.
2. One side → **Digital Pin 2**
3. Same side → 5V
4. Other side → 10k resistor → GND
   (This acts as a pull-down resistor.)

---

## **E. Connect the Buzzer**

1. Positive terminal → **Digital Pin 6**
2. Negative terminal → GND

---

## **F. Connect the LED**

1. LED anode → Digital Pin 3
2. LED cathode → 220Ω resistor → GND

---

## **G. Power/Ground Management**

* Connect Arduino **5V** → Breadboard + rail
* Connect Arduino **GND** → Breadboard – rail
* Make sure all sensors share the same ground.

---





# ✅ **4. Working Principle**

* **LDR** detects light level → Displayed on LCD
* **TMP36** measures temperature → Displayed on LCD
* **Button** acts as a manual trigger → LED + buzzer ON
* **LCD** shows real-time sensor readings

---



# CIRCUIT DIAGRAM:

<img width="1117" height="669" alt="image" src="https://github.com/user-attachments/assets/8bc079d3-34ec-4773-8246-3fdffc3cd51e" />



 
# PROGRAM:
Use this basic template:

```cpp
#include <LiquidCrystal.h>

LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

const int ldrPin = A0;
const int tempPin = A1;
const int buttonPin = 2;
const int ledPin = 3;
const int buzzerPin = 6;

void setup() {
  pinMode(buttonPin, INPUT);
  pinMode(ledPin, OUTPUT);
  pinMode(buzzerPin, OUTPUT);

  lcd.begin(16, 2);
}

void loop() {
  int lightValue = analogRead(ldrPin);
  int tempValue = analogRead(tempPin);

  float voltage = tempValue * (5.0 / 1023.0);
  float temperatureC = (voltage - 0.5) * 100;

  lcd.setCursor(0,0);
  lcd.print("Light:");
  lcd.print(lightValue);

  lcd.setCursor(0,1);
  lcd.print("Temp:");
  lcd.print(temperatureC);

  // Button-controlled LED + buzzer
  if (digitalRead(buttonPin) == HIGH) {
    digitalWrite(ledPin, HIGH);
    tone(buzzerPin, 1000);
  } else {
    digitalWrite(ledPin, LOW);
    noTone(buzzerPin);
  }

  delay(500);
}
```

---

 
# Output:

<img width="1485" height="783" alt="image" src="https://github.com/user-attachments/assets/54ee61d5-4647-43bf-ae56-557e1ef92ba0" />


## Result:
The home automation circuit was successfully simulated in Tinkercad. The LDR and temperature sensor provided real-time light and temperature readings, which were correctly displayed on the LCD. The push button activated the LED and buzzer as expected. All components functioned properly, demonstrating a working prototype of a basic home automation system.

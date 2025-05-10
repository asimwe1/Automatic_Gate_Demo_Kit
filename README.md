

# 🚧 Automatic Gate Demo Kit – Arduino Project

## 📝 Overview

The **Automatic Gate Demo Kit** is an Arduino-based project designed to simulate a real-world automatic gate system. It uses an **ultrasonic sensor** to detect the presence of an object (e.g., a person or vehicle) and automatically opens a gate using a **servo motor**. It also includes **LED indicators** and a **buzzer** to provide visual and auditory feedback during the gate's operation.

This project is perfect for learning basic **Arduino I/O**, **servo control**, **ultrasonic distance sensing**, and implementing **simple real-world automation logic**.

---

## 🔧 Hardware Components

| Component         | Description                      | Arduino Pin             |
| ----------------- | -------------------------------- | ----------------------- |
| Ultrasonic Sensor | HC-SR04                          | Trigger: D2<br>Echo: D3 |
| Red LED           | Indicates gate is closed         | D4                      |
| Blue LED          | Indicates gate is open           | D5                      |
| Servo Motor       | Opens/closes the gate            | D6 (PWM)                |
| Piezo Buzzer      | Sounds when the gate is open     | D12                     |
| Ground Pins       | Software-defined GND connections | D7, D8                  |

---

## 🖥️ Code Functionality

### 🚀 Setup

Upon powering the Arduino:

* The **servo** sets the gate to the **closed position** (0°).
* The **red LED** lights up (indicating the gate is closed).
* The **blue LED** and **buzzer** are off.
* Serial communication begins at **9600 baud**.

### 🔁 Main Loop Workflow

1. **Distance Measurement**:

   * The ultrasonic sensor sends out a pulse and measures the time for it to return.
   * This time is used to calculate the **distance in centimeters**.

2. **Gate Logic** (currently hardcoded):

   * **Gate opens to 80°** regardless of distance (this may be a bug or placeholder logic).
   * **Blue LED** turns ON, **Red LED** turns OFF.
   * A **timer** starts for how long the gate has been open.

3. **Buzzer Behavior**:

   * While the gate is open, the **buzzer toggles** its state (ON/OFF) every 200ms.
   * It stays ON for **800ms** and OFF for **400ms** to create a noticeable pattern.

4. **Gate Closure**:

   * After **5 seconds**, the gate automatically closes:

     * Servo returns to **0°** (closed position)
     * **Red LED** turns ON
     * **Blue LED and buzzer** turn OFF

5. **Loop Delay**:

   * A small `delay(50)` is included to reduce CPU load.

---

## 📦 Pin Configuration Summary

```plaintext
Digital Pins:
 D2 - Ultrasonic Trigger
 D3 - Ultrasonic Echo
 D4 - Red LED (Gate Closed)
 D5 - Blue LED (Gate Open)
 D6 - Servo Motor (PWM Control)
 D7 - Ground (Software)
 D8 - Ground (Software)
 D12 - Piezo Buzzer
```

---

## 🐞 Known Issues / To-Do

* ✅ **BUG**: The ultrasonic `distance` is measured but never actually used in the `if` condition to trigger gate opening. This means the gate opens unconditionally every loop.

  * 🔧 **Fix Suggestion**: Add a condition like `if (distance < threshold)` before opening the gate.
* ✅ **IMPROVEMENT**: Replace `delay()` in buzzer control with non-blocking logic using `millis()`.

---

## 📈 How to Use

1. **Connect the hardware** exactly as described.
2. **Upload the `sketch.ino`** file to your Arduino board.
3. **Open the Serial Monitor** to view distance readings.
4. Move an object near the ultrasonic sensor (once logic is fixed) to trigger the gate.

---

## 🔩 Suggested Improvements

* Add an **LCD screen** or OLED for displaying gate status and distance.
* Use **interrupts** or **state machines** for more efficient control.
* Add **manual override buttons** for open/close.

---

## 🧠 Learning Objectives

* Understand how **servo motors** can simulate mechanical movement.
* Practice **distance sensing** with ultrasonic sensors.
* Build user feedback systems using **LEDs** and **buzzers**.
* Learn **timing control** with `millis()` vs. `delay()`.

---

## 👨‍💻 Author

**Asimwe Landry**

Location: `~/Documents/projects/Automatic_Gate_Demo_Kit`

Feel free to contribute or ask questions!

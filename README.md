# All-In-One_Robot

A 3-in-1 DIY Arduino robot featuring autonomous obstacle avoidance, manual smartphone control via Bluetooth, and hands-free voice navigation. Built using an Arduino Uno, L293D motor shield, ultrasonic sensor, and a Bluetooth module.

## Features

*   **Obstacle Avoidance:** Navigates autonomously by using an HC-SR04 ultrasonic sensor mounted on a micro servo motor to scan the path ahead and evade collisions.
*   **Bluetooth Control:** Allows manual driving via a smartphone controller application connected to the robot's Bluetooth module.
*   **Voice Control:** Enables hands-free navigation by processing spoken commands (e.g., "Go", "Back", "Left", "Right", "Stop") through a smartphone app and transmitting them to the robot.

## Hardware Components

*   Arduino Uno Board
*   L293D Motor Driver Shield
*   HC-SR04 Ultrasonic Sensor
*   HC-05 (or HC-06) Bluetooth Module
*   SG90 Micro Servo Motor
*   4 x DC Gear Motors
*   4 x Robot Wheels
*   2 x 18650 Li-ion Batteries with Holder
*   Jumper Wires
*   Robot Chassis (Foam board, acrylic, or 3D printed)

## Circuit & Wiring Connections

Attach the L293D Motor Driver Shield directly on top of the Arduino Uno.

**DC Motors:**
*   Front Left & Rear Left Motors -> **M4** & **M3** terminals on the L293D Shield
*   Front Right & Rear Right Motors -> **M1** & **M2** terminals on the L293D Shield

**Ultrasonic Sensor (HC-SR04):**
*   **VCC** -> 5V on Shield
*   **GND** -> GND on Shield
*   **Trig** -> Analog Pin **A1**
*   **Echo** -> Analog Pin **A0**

**Servo Motor:**
*   Signal (Orange/Yellow wire) -> Pin **10** on Shield (Servo 1 port)
*   VCC (Red wire) -> 5V
*   GND (Brown/Black wire) -> GND

**Bluetooth Module (HC-05/HC-06):**
*   **VCC** -> 5V on Shield
*   **GND** -> GND on Shield
*   **TXD** -> **RX (D0)** on Shield
*   **RXD** -> **TX (D1)** on Shield

## Software Setup

1.  **Install Required Libraries:** Ensure you have the following libraries installed in your Arduino IDE:
    *   `Servo.h` (Built-in)
    *   `AFMotor.h` (Adafruit Motor Shield library)
2.  **Select the Mode:** In the `loop()` function of the provided `.ino` code, uncomment the specific mode you want to run while keeping the others commented out:
    ```cpp
    void loop() {
      //Obstacle();
      //Bluetoothcontrol();
      //voicecontrol();
    }
    ```
3.  **Upload the Code:** 
    *   **⚠️ IMPORTANT:** You *must* disconnect the RX and TX jumper wires from the Bluetooth module before hitting upload. Leaving them connected will cause an upload error.
    *   Select your board (Arduino Uno) and port, then upload the sketch.
    *   Reconnect the RX and TX wires after the upload is complete.

## Application Setup

To use the Bluetooth or Voice control modes, you will need a Bluetooth controller app on your smartphone.
*   Pair your phone with the HC-05/HC-06 module (default PIN is usually `0000` or `1234`).
*   For **Bluetooth Control**, map your app's directional buttons to send the characters: `F` (Forward), `B` (Backward), `L` (Left), `R` (Right), and `S` (Stop).
*   For **Voice Control**, configure your voice commands to output the corresponding trigger characters defined in the sketch (e.g., `^`, `-`, `<`, `>`, `*`).

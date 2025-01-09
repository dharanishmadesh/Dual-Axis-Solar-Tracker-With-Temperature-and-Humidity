

# **Solar Tracker with Temperature and Humidity Monitoring** 🌞🌡️💧

This project uses a solar tracker system to orient a solar panel based on the light intensity detected by four Light Dependent Resistors (LDRs). It also incorporates a temperature and humidity sensor (DHT11) to display environmental data on an LCD screen. The system adjusts the position of the solar panel using two servos: one for horizontal and one for vertical movement.

---

## **✨ Features**

- **Solar Panel Tracking**: Automatically adjusts the position of the solar panel to maximize sunlight exposure using four LDRs to detect light intensity.
- **Temperature and Humidity Monitoring**: Reads temperature and humidity values using the DHT11 sensor and displays them on an LCD screen.
- **Dual Servo Control**: Two servos (horizontal and vertical) adjust the solar panel's position to follow the sun.
- **LCD Display**: Shows the current temperature and humidity in real time.
- **Automatic Adjustment**: The system continuously adjusts the solar panel based on changes in light intensity.

---

## **📂 Folder Structure**

- `SolarTracker.ino`  
  - Main Arduino sketch file for the solar tracking system with temperature and humidity monitoring.
- `README.md`  
  - Documentation for the project.
- `LICENSE`  
  - Open-source license details (if applicable).

---

## **🔧 Hardware Components**

- **Arduino Board** (e.g., Arduino Uno or Nano)
- **2x Servo Motors** (for horizontal and vertical movement)
- **4x Light Dependent Resistors (LDRs)**
- **DHT11 Temperature and Humidity Sensor**
- **16x2 LCD Display** (with I2C interface)
- **Jumper wires**
- **Breadboard** (optional)
- **Power supply** (e.g., 9V battery or USB power)

---

## **🔌 Circuit Connections**

| Component                | Pin Assignment   |
|--------------------------|------------------|
| **Horizontal Servo**      | Pin 9            |
| **Vertical Servo**        | Pin 10           |
| **LDR 1 (Top Left)**      | Pin A0           |
| **LDR 2 (Top Right)**     | Pin A1           |
| **LDR 3 (Bottom Left)**   | Pin A2           |
| **LDR 4 (Bottom Right)**  | Pin A3           |
| **DHT11 Sensor**          | Pin 8            |
| **LCD Display**           | Pins 12, 11, 5, 4, 3, 2 |
| **Buzzer**                | Pin 2            |

---

## **⚙️ Software Requirements**

- Arduino IDE (version 1.8.10 or later)

---

## **🚀 How to Use**

1. **Setup**  
   - Connect the LDRs, servos, DHT11 sensor, and LCD to the Arduino board as described in the circuit section.
   - Power the Arduino with a suitable power source (e.g., battery or USB).

2. **Upload Code**  
   - Open the `SolarTracker.ino` file in Arduino IDE.
   - Select the correct board and port under **Tools**.
   - Upload the code to your Arduino board.

3. **Operation**  
   - The system will begin by positioning the solar panel to face the sunlight.
   - The LCD will display the current temperature and humidity.
   - The servos will adjust the panel based on changes in light intensity.

---

## **💡 Code Overview**

This code uses four LDRs to track light intensity from different directions. Based on the readings from the LDRs, the system adjusts the position of the servos to orient the solar panel towards the brightest direction. The temperature and humidity readings are also displayed on the LCD screen.

### **Main Code Logic**

1. **LDR Readings**  
   The code calculates the average light intensity from the top and bottom sensors, as well as the left and right sensors. If there's a difference in the light intensity, the corresponding servo (horizontal or vertical) will adjust the position.

2. **Temperature and Humidity**  
   The DHT11 sensor is used to read temperature and humidity values, which are displayed on the LCD screen.

3. **Servo Control**  
   The horizontal and vertical servos are controlled by adjusting their angles based on the LDR readings.

```cpp
int avt = (lt + rt) / 2; // Average value from top LDRs
int avd = (ld + rd) / 2; // Average value from bottom LDRs

int dvert = avt - avd;   // Difference between top and bottom
int dhoriz = avl - avr;  // Difference between left and right

if (dvert > tol) {
    // Adjust vertical servo angle
    vertical.write(servov);
}

if (dhoriz > tol) {
    // Adjust horizontal servo angle
    horizontal.write(servoh);
}
```

---

## **📜 License**

This project is licensed under the **MIT License**. See the `LICENSE` file for details.

---

## **🤝 Contributing**

Contributions are welcome! You can:
- Submit a pull request with new features or bug fixes.
- Open an issue to report bugs or suggest improvements.

---

## **💬 Feedback**

For questions, suggestions, or feedback, feel free to open an issue or contact me directly.

---

This project aims to maximize solar energy capture by dynamically positioning the solar panel towards the sun, while also providing real-time environmental data for monitoring temperature and humidity.

---

Stay Green and Powered! 🌱🔋

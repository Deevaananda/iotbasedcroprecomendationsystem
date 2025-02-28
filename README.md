# Smart Agriculture Monitoring System

## Overview

This project implements a smart agriculture monitoring system using an ESP8266 and various sensors to collect environmental data and provide recommendations for optimal crop growth. The system monitors temperature, soil moisture, pressure, and altitude, displaying the data on a web interface and offering economic analysis and crop suggestions.

## Features

*   **Real-time Monitoring:** Displays real-time data for temperature, soil moisture, pressure, and altitude on a web interface.
*   **Data Visualization:** Uses Chart.js to create interactive charts for visualizing sensor data over time.
*   **Recommended Crop:** Suggests an optimal crop based on current soil moisture, temperature, and pressure conditions.
*   **Economic Analysis:** Provides estimated cost, projected profit, and water usage calculations for the recommended crop.
*   **Web Interface:** User-friendly web interface built with HTML, CSS, Bootstrap, and Tailwind CSS.
*   **Data Export:** Allows users to export sensor data for further analysis.
*   **Theme Toggle:** (Commented out in code, but potentially implementable) Allows users to switch between light and dark themes.

## Hardware Components

*   ESP8266 (e.g., NodeMCU, Wemos D1 Mini)
*   BMP180/BMP085 Barometric Pressure Sensor
*   Soil Moisture Sensor

## Software Components

*   Arduino IDE
*   ESP8266WiFi library
*   Adafruit BMP085 library
*   ESP8266WebServer library
*   ArduinoJson library

## Connections

*   **BMP180/BMP085 Sensor:**
    *   SDA to ESP8266 SDA (typically D2)
    *   SCL to ESP8266 SCL (typically D1)
    *   VCC to ESP8266 3.3V
    *   GND to ESP8266 GND
*   **Soil Moisture Sensor:**
    *   Analog Output to ESP8266 A0
    *   VCC to ESP8266 3.3V
    *   GND to ESP8266 GND

**Important:**  Double-check the pinout of your specific ESP8266 board. You may need to install pull-up resistors for I2C communication if your board doesn't have them.

## Installation and Setup

1.  **Install Arduino IDE:** Download and install the Arduino IDE from the official Arduino website ([https://www.arduino.cc/](https://www.arduino.cc/)).
2.  **Install ESP8266 Board Support:**
    *   Open Arduino IDE and go to `File > Preferences`.
    *   Add the following URL to "Additional Board Manager URLs":  `http://arduino.esp8266.com/stable/package_esp8266com_index.json`
    *   Go to `Tools > Board > Boards Manager...` and search for "ESP8266". Install the `esp8266 by ESP8266 Community` package.
3.  **Install Libraries:**
    *   Go to `Sketch > Include Library > Manage Libraries...`
    *   Search for and install the following libraries:
        *   `ESP8266WiFi` (Should be included with the ESP8266 board support)
        *   `Adafruit BMP085` (or `Adafruit BMP180`, if available)
        *   `ESP8266WebServer`
        *   `ArduinoJson`
4.  **Connect Hardware:** Connect the sensors to the ESP8266 according to the pinout described above.
5.  **Upload Code:**
    *   Open the Arduino sketch in the Arduino IDE.
    *   Modify the `ssid` and `password` variables in the code to match your Wi-Fi network credentials.
    *   Select your ESP8266 board from `Tools > Board`.  (e.g., "NodeMCU 1.0 (ESP-12E Module)")
    *   Select the correct port from `Tools > Port`.
    *   Upload the code to the ESP8266.
6.  **Access Web Interface:**
    *   Open the Serial Monitor in the Arduino IDE (Tools > Serial Monitor).
    *   After the ESP8266 connects to Wi-Fi, it will print its IP address.
    *   Open a web browser and enter the ESP8266's IP address in the address bar.

## Configuration

*   `soilMoistureDry`: Adjust this value to reflect the analog reading of the soil moisture sensor in completely dry conditions.
*   `soilMoistureWet`: Adjust this value to reflect the analog reading of the soil moisture sensor when fully submerged in water.
*   The `recommendCrop()` function will need to be customized with logic to suggest appropriate crops for your specific environment.
*   `calculateCost()`, `calculateProfit()`, and `calculateWaterUsage()` should be adapted with realistic values for your region.

## Code Structure

*   **`setup()`:** Initializes serial communication, connects to Wi-Fi, initializes the BMP180 sensor, and starts the web server.
*   **`loop()`:** Handles client requests to the web server.
*   **`handleWebpage()`:** Sends the HTML content for the web interface to the client.
*   **`handleData()`:** Collects sensor data, formats it as JSON, and sends it to the client.
*   **`recommendCrop()`:** (To be implemented) Recommends a crop based on sensor readings.
*   **`calculateCost()`:** (To be implemented) Calculates the estimated cost of growing the recommended crop.
*   **`calculateProfit()`:** (To be implemented) Calculates the projected profit from the recommended crop.
*   **`calculateWaterUsage()`:** (To be implemented) Estimates the water usage for the recommended crop.

## To-Do

*   Implement the `recommendCrop()`, `calculateCost()`, `calculateProfit()`, and `calculateWaterUsage()` functions with relevant logic and data for your region.
*   Add error handling and improve data validation.
*   Implement the theme toggle functionality.
*   Consider adding data logging to a database or cloud service.
*   Add calibration routines for the sensors.

## Contributing

Contributions are welcome!  Please fork the repository and submit a pull request with your changes.

## License

[Choose a license, e.g., MIT License]

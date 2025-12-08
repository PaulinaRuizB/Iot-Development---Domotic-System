# Iot-Development: Domotic-System
This repo contains the implementation of a Domotic System through the free firmware called ESPHome and Home Assistant.

# IoT Environmental Monitoring System with ESP32-C6 and Home Assistant

This project implements a distributed IoT architecture using **ESP32-C6 sensor nodes** that capture environmental variables and send them to a **central Home Assistant server** running on a **BeaglePlay**.
The system measures temperature, humidity, atmospheric pressure, gas levels, and light intensity, providing real-time monitoring and historical data visualization.

---

## System Architecture Overview

The system is structured into several technological layers:

| Layer             | Technologies                  | Description                                         |
| ----------------- | ----------------------------- | --------------------------------------------------- |
| **Physical**      | Wi-Fi → ESP32-C6 ↔ BeaglePlay | Wireless communication between nodes and the server |
| **Network**       | Wi-Fi                         | Connects each node to the Home Assistant server     |
| **Transport**     | TCP                           | Reliable delivery of sensor messages                |
| **Application**   | ESPHome API or MQTT           | Data publishing and device control                  |
| **Data**          | Home Assistant                | Entity management and device discovery              |
| **Visualization** | SQLite / InfluxDB / Grafana   | Dashboards, charts, and analytics                   |

---

## Main Components

### **ESP32-C6**

A Wi-Fi microcontroller acting as a sensing node.
Responsibilities include:

* Reading attached sensors
* Sending data via ESPHome API or MQTT
* OTA (over-the-air) firmware updates
* Executing small automation routines

---

### **Sensors Included**

| Sensor         | Measured Variables              | Notes                                          |
| -------------- | ------------------------------- | ---------------------------------------------- |
| **DHT11**      | Temperature, Humidity           | Basic, slow response, needs a pull-up resistor |
| **BME280**     | Temperature, Humidity, Pressure | High precision, I²C mode needs CSB = 3.3V      |

## Connection to Home Assistant

### **ESPHome API**

Provides:

* Automatic device discovery
* Realtime logs
* OTA updates

Example YAML:

```yaml
api:
  encryption:
    key: "YOUR_KEY_HERE"
ota:
```

In Home Assistant:
**Settings → Devices & Services → ESPHome → Add Device**

Your ESP32-C6 will appear automatically.

## Data Flow

1. ESP32-C6 reads temperature, humidity and pressure.
2. Data is serialized and sent via Wi-Fi.
3. Home Assistant receives the sensor states.
4. Values are stored in SQLite.
5. Dashboards visualize:

   * Temperature trends
   * Humidity variation
   * Pressure differences
   * Gas detection alerts
   * Motion-triggered events

## Architecture

<img width="1920" height="1080" alt="Nodo Secundario" src="https://github.com/user-attachments/assets/a650c1b3-53b6-442c-996f-6615d3e20650" />

## Physical Implementation

<img width="1240" height="360" alt="image" src="https://github.com/user-attachments/assets/9a857018-975d-4360-afbc-b7ea042ed580" />


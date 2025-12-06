## ESP32-C6 IoT Node – Environmental Monitoring

This project implements an ESP32-C6 IoT node capable of reading environmental data. It is designed to work with the ESP-IDF framework and uses Wi-Fi to communicate with an MQTT broker.

### **Main Features**

* **Sensor Support**

  * Reads temperature and humidity using either a **DHT11** or **BME280** sensor.
  * The code includes the necessary YAML lines to add more sensors. 
  * Automatically parses and publishes sensor data to MQTT topics such as:

    * `home/node1/temperature`
    * `home/node1/humidity`

* **MQTT Communication**

  * Publishes sensor data periodically.
  * Receives color commands in JSON format (e.g., `{ "r": 255, "g": 0, "b": 128 }`).
  * Includes automatic reconnecting on connection drops.

* **Asynchronous Task Structure**

  * Dedicated FreeRTOS tasks for:

    * Sensor reading
    * MQTT handling
    * LED rendering
  * Ensures smooth performance and responsiveness.

### **How It Works**

1. The ESP32-C6 connects to Wi-Fi and initializes the MQTT client.
2. A background task reads the sensor periodically and publishes the data to MQTT.
3. The device listens for incoming MQTT messages to update the LED color in real time.

### **Use Cases**

* Home environmental monitoring
* Smart LED lighting
* IoT dashboards or automation systems
* Educational and prototype projects


## Home Assistant & ESPHome Setup

The setup uses:

* A **BeaglePlay board** running *Home Assistant OS (Supervisor)* via Ethernet
* A **local computer** running an ESPHome Docker container to edit and compile YAML configurations

### **1. Installing Home Assistant Supervisor on the BeaglePlay**

1. Connect the BeaglePlay to your network using an Ethernet cable.
2. Flash Home Assistant OS (Supervisor edition) onto the device’s storage.
3. Boot the board and access Home Assistant from your browser:

   ```
   http://homeassistant.local:8123
   ```
4. Complete the initial setup (user account, home config, etc.).

Home Assistant Supervisor gives you:

* Add-on management
* Automatic updates
* Full integration with ESPHome, MQTT, dashboards, and automations

### **2. Running ESPHome Using Docker (Local Computer)**

On your main computer, ESPHome is not installed directly — it runs inside a Docker container. This allows you to open the ESPHome Dashboard and edit all `.yaml` files for your ESP32-C6 node.

**Run ESPHome with Docker:**

```bash
docker run --rm -it \
  -v "${PWD}/esphome:/config" \
  -p 6052:6052 \
  esphome/esphome
```

After the container starts, open in your browser:

```
http://localhost:6052
```

From this dashboard you can:

* Create and edit YAML configurations
* Compile and flash firmware to the ESP32-C6
* View logs in real time
* Send OTA updates directly into Home Assistant

### **3. Connecting ESPHome With Home Assistant**

Once the ESP32-C6 firmware is compiled:

1. Flash the device via USB from the ESPHome dashboard.
2. The device will automatically appear in **Home Assistant → Integrations**.
3. Add it with one click to enable:

   * Temperature & humidity sensor entities
   * LED control entities
   * Device status and diagnostics

### **4. Visualizing Data in the Dashboard**

In Home Assistant:

1. Go to **Overview → Edit Dashboard**
2. Add new cards such as:

   * *Gauge* for temperature
   * *Sensor* cards for humidity
   * *Light* card to control the WS2812 LED
3. Group entities into a clean dashboard for monitoring and control.



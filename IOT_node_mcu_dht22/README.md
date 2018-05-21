# Raspberry PI 3
# Temperature & Humidity Sensor Node Installation
# Using a nodeMCU-Amica board

## Preliminars

1. Download and install latest Arduino IDE: https://www.arduino.cc/en/Main/Software

2. Go to Preferences and set platform extension JSON:

`http://arduino.esp8266.com/stable/package_esp8266com_index.json`

![preferences](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/arduino_ide_setup.jpg)

3. Go to tools -> boards -> boards manager, and search for "nodeMCU". Download the packet: 

![Boards Manager](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/arduino_ide_setup.jpg)

Set "NodeMCU v1.0" as our working board.

4. Plug your nodeMCU to your laptop, go to tools -> Port, and select your USB Port.

5. Open "IOT_node_mcu_dht22.ino" sketch in IDE. 

6. Open thingsboard dashboard in your browser and add a new Device:

![Add Device](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/dashboard_add_device.png)

7. Copy its ACCESS TOKEN and use it to configure arduino sketch.

![Get Token](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/dashboard_access_token.png)
7. Compile it. If necessary download and install necessary libraries.

8. Upload sketch to nodeMCU with DHT22 Connected according to following schema:

![Upload](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/arduino_ide_upload.png)

9. Go to thingsboard panel and check "Last telemetry" data from your device. If it is updated everything is working fine.

![Test Device](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/dashboard_test_device.png)

10. You can also check serial monitor from Arduino IDE. It shows relevant information in case something is wrong.

![Serial check](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_node_mcu_dht22/images/arduino_ide_serial.png)

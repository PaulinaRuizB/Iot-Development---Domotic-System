# Iot-Development---Domotic-System
This repo contains the implementation of a Domotic System through the free firmware called ESPHome and Home Assistant.

## Description: 

This project implements a Domotic System using the open source firmware ESPHome and Home Assistant. Basically, consist of secundaries nodes with the ESP32C6 board that receive the data of interest from the sensors BME280 (to monitor the temperatue and atmospheric pressure) and the DHT11 (to monitor humidity). Those data are processed for the main node controlled by the Beagleplay board and send to the Home Assistant platform, where the user can make decisions about what to do in case of register anomalous data. Through this platform it is possible to store the data for a determinate time and to watch different graphics of the system´s behavior.

## Funcionality 

- The secundaries nodes are programmed through the language YAML, a very easy way to understand the code and to control the actions to execute. Each sensor has its own code to define the variales, time of response and actions. This YAML code is send to the main node (the BeaglePlay), where is processed

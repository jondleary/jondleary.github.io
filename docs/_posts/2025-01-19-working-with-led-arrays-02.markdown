---
layout: post
title:  "Working with the WS2812B LED Array (LED Display #2)"
date:   2025-01-19 17:30:00 -0800
categories: LED Display
---
  
Part 2 of [Designing a WiFi enabled LED Array Weather Display](https://jondleary.github.io/led/display/2025/01/19/wifi-led-array-display-01.html).  
  
## Choosing an MCU  
  
As the display will require internet access to collect the weather data an MCU with WiFi capability must be selected. For wide ranging support and ease of programming either an ESP32 or ESP8266 will be used, or alternatively a RP2040-W or analogous device could be used.   
  
## Sending data to the LEDs  
   
The WS2812B LEDs ar individually addressable. They use a custom single wire communication protocol and this one wire can be used to control each of the LEDs on the array. The Data In wire is connected to the Data In pin of the first LED of the array, the data out pin of this LED is connected to the Data In pin of the next LED and so on for each subsequent LED in the array.

The LEDs are set up in a serpentine pattern beginning at the top left of the array and then alternately working down and back up each subsequent column like so:  
![Image]({{"assets/images/led-weather/led-array-snake.jpg",  | relative_url }})   




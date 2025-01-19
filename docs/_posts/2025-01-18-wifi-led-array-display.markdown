---
layout: post
title:  "Making a WiFi enabled LED Array based Weather display (LED Display #1)"
date:   2025-01-18 17:37:00 -0800
categories: LED Display
---
  
This is the first post in a series documenting the development of a WiFi enabled LED array based display. The display will be used to show the current local weather forecast, provide indicators for Fire and Wind warnings, as well as likelihood of precipitation.  
  
## What is an LED Array?  
  
The LED array I will be using is a commonly available array of WS2812B programmable RGB LEDs on a flexible PCB substrate. The array in question is 8x32 LEDs (Amazon PN ASIN:B01DC0IPVU). Other sizes are available.  
Here is the link used to purchase it: https://www.amazon.com/BTF-LIGHTING-0-24ft0-96ft-Flexible-Individually-addressable/dp/B01DC0IPVU  
  
![Image]({{"assets/images/led-weather/8x32-led-array.jpg",  | relative_url }})  
  
## Why use an LED Array?  
  
Why use an LED array rather than an LCD, OLED, smartphone, or similar display which can show far more detailed text and numbers? 
While cost could be a major factor, the primary reason for using an LED array is for the ease and potential speed of information transfer. For example an LED array by the front door of your home with an indicator light for chance of rain would be an almost instant reminder to grab your umbrella. The colour and intensity of the LEDs might be a quick visual indicator that today will be hot and you don't need your jacket. An indicator light for a High Wind alert might remind you to secure some items in your garden.  
Some secondary reasons are:   
1. Glowing LEDs are cool.   
2. It's a good excuse to learn a range of skills including embedded programming, web APIs, 3D CAD and printing etc.  
3. I have an LED array already...  
  
  
## Development process

0. Concept generation.
1. Define requirements: What do we want the display to do?  
2. Define initial specifications: What do we need to do to meet the functions set out in the requirements?  
3. Prototype: Make an initial minimum viable prototype to use for POC testing and feed back into the specifications.  
4. Design: Take learnings from prototype stage and do the HW/FW development to create a full device.
5. Test: Test the device to identify issues and ensure that it meets the specifications.
6. Iterate: Repeat steps 4 and 5 until satisfied. (This is a one off device so no need for DFM/scalability etc. beyond that needed to produce a working and cosmetically acceptable device.)


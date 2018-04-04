---
author: "Joshua Mangiola"
date: 2018-03-29
linktitle: Super Cheap REST API on a chip (ESP32 Arudino aREST Guide)
menu:
  main:
    parent: tutorials
title: Super Cheap REST API on a chip (ESP32 Arudino aREST Guide)
description: This tutorial will be an getting started guide to the ESP32 and aREST that I have written as I have been playing around with the ESP32
weight: 10
---

## **Introduction**

This tutorial will be an getting started guide to the ESP32 and aREST that I have written as I have been playing around with the ESP32

The Completed Code for this tutorial is avaliable [here](http://github.com) for download 
<!--more-->

I recently bought an ESP32 NodeMCU Module off eBay for around $10-15 just to play around with and I have found that this little chipset is capable of so much. Here is a brief rundown of the specs that the device has, The full specs can be found on the [datasheet here](https://www.espressif.com/sites/default/files/documentation/esp32_datasheet_en.pdf)

>* CPU: Xtensa dual-core (or single-core) 32-bit LX6 microprocessor, operating at 160 or 240 MHz and performing at up to 600 DMIPS
>* Memory: 520 KiB SRAM
>* Wi-Fi: 802.11 b/g/n
>* Bluetooth: v4.2 BR/EDR and BLE
>* 12-bit SAR ADC up to 18 channels
>* 2 × 8-bit DACs

Expressif was able to pack alot into this little SOC for the price in my opinon. The chipset is much cheaper on its own but for starting development with this SOC i'd reccommend getting a module like the one I bought as it allows for easy uploading of code via USB.

For this simple task I will be using Arduino as it has less of a difficulty curve then the ESP-IDF Offical SDK from ExpressIf, and there is also Simba and MicroPyhton if you like to be different.

## IDE

It has been many years since I last used the awful Arduino IDE which I feel like is inbetween Notepad and NotePad ++ in terms of features, so when I started this project I found out about [PlatformIO](http://www.platformio.org). This is a game changer for me as I can now use VS Code which makes the learning curve almost non existant for the IDE part. 

To get started with PlatformIO we are Just going to install the Extension from the marketplace and wait for it to dowload its dependancies and automatically install. Once you see the Platform IO default screen in VS Code just hit New Project and under Boards look for the ESP32 type you have. Mine was the ESP32 NodeMCU, once that is selected the third box needs to be Arduino then click continue and wait for it to download all the dependancies for the board.

## Starting to Code :)

Now once the project is loaded we need to add the aREST dependancy to the project which Platform.io makes a breeze, this is done simply by going to the PlatformIO Home then selecting libraries and searching for aREST by marcoschwartz then selecting install and its done, told you it was easy.






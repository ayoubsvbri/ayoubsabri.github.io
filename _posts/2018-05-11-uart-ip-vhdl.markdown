---
title: "UART IP implementation in VHDL with ultra-sound sensor reference design"
layout: post
date: 2018-05-11 12:15
tag:
- VHDL
- FPGA
- UART
- RS232
image: # add image here
headerImage: true
projects: true
hidden: false # don't count this post in blog pagination
description: ""
category: project
author: ayoubsabri
externalLink: false
---

![Screenshot](https://imgur.com/vgQXNkq.png)

---

## Repository

You can find the source code and documentation [here](https://github.com/AyoubSabri/uart-ip-vhdl).

---

## Overview

This IP Core is an implementation of the _Universal Asynchronous Receiver/Transmitter_
(UART) protocol. This core is designed for FPGA and ASIC that need to interface with other
devices and who share this standard.

A reference design has been provided in order to test the system using an ultra-sound sensor and send the measurement to an external device. Please read documentation for more details.

---

## Features

Here are the main features:

- Single channel UART
- Programmable baud rates: 9600, 19200, 38400, 57600, 115200 bps
- 8-N-1 format: 1 start bit, 8 bits data, no parity bit, 1 stop bit
- Entirely portable IP
- Fully synchronous design

---

## Reference design

A reference design has been included in the repository. The example read data from an ultra-sound distance sensor and send the measured value in cm through the UART transmission line.

---

## Deliverables

- Synthesizable VHDL source code
- Basic verification testbenches
- Detailed user guide

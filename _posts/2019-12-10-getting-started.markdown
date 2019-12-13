---
title: "week 0: getting started"
layout: post
date: 2019-12-03 12:00
image: /assets/images/markdown.jpg
headerImage: false
tag:
- stm32
- blinky
- LED
- MCU
category: blog
author: ayoubsabri
description:
---

## introduction

This post is the first of a series in which I will cover some basic aspects of software development on microcontrollers. Everything you need if you want to apply the insights shown in this series is a stm32 board. Personally I will be using a _STM32L452_ from _STMicroelectronics_ which comes with a Cortex-M4 core at 80 MHz, 512 kb of flash memory and 160 kb of SRAM. This microcontroller also integrates various peripherals:

- GPIO
- USART
- I2C
- SPI
- DMA
- ADC/DAC
- timers
- watchdog
- and many others...

In this collection of tutorials I will try to explore as much of them as I can.
Today you will see how to setup a project from scratch with _STM32CubeMX_ and make a LED blink.

## setup the toolchain

I really recommend [this][1] guide. It has been written for _macOS_ but it shouldn't be that different for _Linux_. Follow the steps and at the end you should have installed on your machine:
- _GNU ARM toolchain_ (compiler, debugger and others...)
- _STCubeMX_ (makefile generation, Hardware Abstraction Layer and Low Level drivers)
- _STCubeProgrammer_ or _st-flash_ (flash/program your board)
- _st-util_ (allows to launch a gdb server for debugging)

## create a project

In this section I will show you how to create and setup a project on _STM32CubeMX_.
First of all, launch the software and when you get to main view click on _ACCESS TO BOARD SELECTOR_ (a new page will appear). Select your board from the list and validate your choice by clicking on the _Start Project_ button. Again, I will use the _NUCLEO-L452RE-P_ development kit.

![Image](/assets/images/blog/0/board.png)

When you're asked if you want to configure the peripherals to their default mode choose _yes_.

![Image](/assets/images/blog/0/init.png)

Now move to the _Project Manager_ tab, choose a name for your project, a location and set the _Toolchain/IDE_ field to _Makefile_ (it's easier to manage small projects with makefiles).

You should now see in the pinout view that some peripherals have already been configured for us. As I mentioned before, we're going to use only the default LED and make it blink.

![Image](/assets/images/blog/0/config.png)

Generate the code by clicking on the _Generate Code_ button on the top right corner of the window.
Open `main.c` with your favourite IDE and explore the code. You should see that some functions have been added to the file that do some basic initialization for the enabled peripherals (the ones in green in the previous image).
Next, add the following lines to the infinite loop to make the LED blink:

```c
while(1){
    HAL_GPIO_WritePin(GPIOB, GPIO_PIN_13, GPIO_PIN_RESET);  // LED off
    for (size_t i = 0; i < 500000; i++) { }                 // wait

    HAL_GPIO_WritePin(GPIOB, GPIO_PIN_13, GPIO_PIN_SET);    // LED on
    for (size_t i = 0; i < 500000; i++) { }                 // wait
}
```

## compile and flash

Open a terminal and move to the directory that contains the makefile and run:

```
$ make -j 4
```

The `-j n` option allow to run this process on `n` different jobs in order to run it faster. It's recommended to run this command with `n` equal to the number of cores in your processor.

When the compilation is finished, a new `build` directory will be created and it will contain all the binary files in different file extensions (.hex, .bin, .elf).

The last thing to do is to transfer the binary to the microcontroller's memory. To do this we're going to use _st-flash_, running:

```
$ st-flash --format ihex write ./build/*.hex
```

or using:

```
$ st-flash write ./build/*.bin 0x08000000
```

...and here is the result:

<iframe src="https://giphy.com/embed/Ut8474RhAb6CCtpF2f" width="270" height="480" frameBorder="0" class="giphy-embed" allowFullScreen></iframe>

Hope you enjoyed it! See you soon in the next article :)

## references

- [STM32 with macOS][1]


[1]: https://github.com/glegrain/STM32-with-macOS

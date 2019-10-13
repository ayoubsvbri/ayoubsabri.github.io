---
title: "Assembly implementation of Samegame"
layout: post
date: 2018-01-27 12:15
tag:
- assembly
- MIPS
- samegame
image: # add image here
headerImage: true
projects: true
hidden: false # don't count this post in blog pagination
description: ""
category: project
author: ayoubsabri
externalLink: false
---

![Screenshot](https://upload.wikimedia.org/wikipedia/commons/4/4f/SameGame.jpg)

---

## Repository

You can find the source code [here](https://github.com/AyoubSabri/samegame).

---

## Description

Samegame is a puzzle game released in 1985 in Japan by Kuniaki Moribe. The rules are very simple:

> SameGame is played on a rectangular field, typically initially filled with four or five kinds of blocks placed at random. By selecting a group of adjoining blocks of the same color, a player may remove them from the screen. Blocks that are no longer supported will fall down, and a column without any blocks will be trimmed away by other columns always sliding to one side (often the left). The goal of the game is to remove as many blocks from the playing field as possible.

_from [wikipedia](https://en.wikipedia.org/wiki/SameGame)_

As part of a school assignment of computer architecture class I had to implement this game in assembly. The target architecture was MIPS, a 32 bit processor with a reduced set of instructions (RISC).

In the future I will probably write a blog post where I will detail the algorithm behind the game and provide some explanations about on assembly programming, stay tuned!

---

## Setup

In order to execute the code you will need to install [MARS](http://courses.missouristate.edu/kenvollmar/mars/download.htm) on your machine, a MIPS that you can execute on all platforms with Java. MARS is an IDE that allows you to simulate and execute MIPS instructions. The only thing you need to do is to open the file _samegame.asm_ and to click on Run. Then just follow the instructions on the console and enjoy the game 😁

---
layout: post
tags: 
- n64
- radare2
- tools
title: N64 Rom Analysis with Radare2 
thumbnail: /public/consoles/Nintendo 64.png
image: /public/n64radare2.png
permalink: /n64-radare2
breadcrumbs:
  - name: Home
    url: /
  - name: Nintendo 64
    url: /n64
  - name: N64 Rom Analysis with Radare2
    url: #
recommend: ps1
editlink: /n64/n64_Radare2.md
---
This guide will presume you have already installed the radare2 suite of binary analysis tools on your computer.

# Opening an N64 executable in radare2
First lets run radare2:
```bash
r2 ./biglevel.z64
```

Replace biglevel.z64 with the location of your own  N64 ROM.

Now we want to analyze all the functions in the executable like so:
```
aaaa
```

Now we can get a list of all the functions found by Pressing v twice:
￼

# Renaming Official SDK Symbols
Having all the functions named fcn.<hex Location> is not very helpful, so lets find the function names for the Official N64 SDK as pretty much every game was compiled and used most of these functions.
**TODO**

# Renaming Common Sample Functions
It is common for developers to copy and paste sample code so lets see if we can match any sample code function names in this rom.
**TODO**

So now you will be left with a bunch of game specific functions that can’t be renamed (unless you have a linker map file). So the real reverse engineering starts!

We need to use a mixture of radare2, emulator and memory editors to try to figure out what to call these functions.

We will never be able to get the original name of the function unless but by debugging the game in an emulator we can make good guests as to what they should be called.

## Use the SDK symbols
One way to find out what a function does is look at the standard SDK functions it uses (thanks to the symbols we imported earlier).

If for example the function makes lots of called to Graphics libraries then you can be sure this function is used for rendering the game and so on.

The same applies for pretty much all standard APIs as it is unlikely developers will mix playing audio with saving the game to memory card for example.

## Use the Strings
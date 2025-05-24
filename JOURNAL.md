---
title: "Keyboard-With-Utiliyy"
author: "DHMango"
description: "A mechanical keyboard that has a screen and you can plug a mouse into"
created_at: "2025-05-23"
---

#May 23: It begins.
After thinking for a little while, I settled on a mechanical keyboard with an LCD and some USB ports. This will be my first time designing a PCB, and I don't want to choose something to diffifult, but I think this should be doable and pretty cool. To start, I looked online for similar designs, and found some things I can potentially use as reference. (https://github.com/zli117/Pico-Keyboard?tab=readme-ov-file, https://hackspace.raspberrypi.com/articles/how-i-made-a-pcb-mechanical-keyboard, and https://jams.hackclub.com/batch/usb-hub/part-1). I decided to use KiCad to design the PCB because it seems pretty widely used is free. 

I am going to use a Rapsberry Pi Pico because of its small form factor, low price, and popular use in similar projects. It looks like if I want to be able to split the USB input, I will need to have the Pi Pico connected downstream of something else, so I won't be able to use the USB connector it comes with. Based on the datasheet, though, I should be able to surface mount it onto the PCB and use the test points to make a connector. Looking online, it seems like I can apply solder paste to the PCB, place the Pico on, and heat it up with a hot air soldering gun. Unfortunately, these cost around $30 so I may have to find some workaround. It seems kind of janky, but it might be better to just use a cable that plugs into the pico but is attatched internally. If I can't get this to work, I may have to abandon the extra ports :(

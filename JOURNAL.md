---
title: "Keyboard-With-Utility"
author: "DHMango"
description: "A mechanical keyboard that has a screen and you can plug a mouse into"
created_at: "2025-05-23"
---

# May 23: It begins. Some planning and schematic work.

After thinking for a little while, I settled on a mechanical keyboard with an LCD and some USB ports. This will be my first time designing a PCB, and I don't want to choose something to diffifult, but I think this should be doable and pretty cool. To start, I looked online for similar designs, and found some things I can potentially use as reference. ([Pi Pico Keyboard](https://github.com/zli117/Pico-Keyboard?tab=readme-ov-file), [PCB Keyboard](https://hackspace.raspberrypi.com/articles/how-i-made-a-pcb-mechanical-keyboard), and [USB hub](https://jams.hackclub.com/batch/usb-hub/part-1)). I decided to use KiCad to design the PCB because it seems pretty widely used is free.

I am going to use a Rapsberry Pi Pico because of its small form factor, low price, and popular use in similar projects. It looks like if I want to be able to split the USB input, I will need to have the Pi Pico connected downstream of something else, so I won't be able to use the USB connector it comes with. Based on the datasheet, though, I should be able to surface mount it onto the PCB and use the test points to make a connector. Looking online, it seems like I can apply solder paste to the PCB, place the Pico on, and heat it up with a hot air soldering gun. Unfortunately, these cost around $30 so I may have to find some workaround. It seems kind of janky, but it might be better to just use a cable that plugs into the pico but is attatched internally. If I can't get this to work, I may have to abandon the extra ports :(

After spending a little while trying to input pcb elements into kicad, I decided to just use EasyEda, because it is also free, seems easier, and many of the LCSC components easily available. Unfortunately, I am having some problems understanding the pinout of the USB-C connector which I want the keyboard to connect with. I have to go to bed now, but this is what I have so far. 

![](https://hc-cdn.hel1.your-objectstorage.com/s/v3/be045fe81315f0288636f58adefc04a6cdf7124f_screenshot_2025-05-24_002139.png)

Today, work has been somewhat slow, but I think it should start to go better once I have this software figured out.

**4 hrs**

# May 24: Schematics

Today I want to mostly finish the schematics, at least for the keyboard part. Last time, I forgot to save my schematic, but it is fine, because I only made slight progresss. Since I want to use USB-C, I needed to figure out what the special pins are for. It seems like many of them can be shorted, but CC1 and CC2 need to be pulled down. Next, I looked on the components catalog and found what I was looking for earlier: 4 pin wire to board connector. This should let me plug the Pico in without needing the test points. I made a test PCB to see about specific parts, and everything is fine except for the Pico, which it can only make the pads for (assembly costs +$50), so I will solder it on manually. I also added the USB-A ports for mice and etc.. It is taking a while to find the correct components and figure out how to read the spec sheets, but I think I am getting a hang of it. This is what I have so far.

![](https://hc-cdn.hel1.your-objectstorage.com/s/v3/d33dd988320a5a328f591fa9a7b45f70af6fc251_image.png)

Thinking more about the display on the keyboard, I think that I will make it be a "Now Playing" thing like [this Spotify display](https://github.com/Dongathan-Jong/SpotifyDisplay/?tab=readme-ov-file) 

**2.5 hrs**

 # May 25: Key layout

 Now, it is time to make the keyboard. I used keyboard-layout-editor.com to generate a layout that I like. After doing some reasearch I think that I am going to use a slightly modified 75% keyboard with space for the screen that I want to add. I think I will use [these keycaps](https://www.amazon.com/dp/B0D1QYXBNV?th=1) because they look cool and are pretty cheap. They also support many keyboard layouts. 
 
 ![](https://github.com/user-attachments/assets/fae62950-9944-42f3-984f-2ff54f396937)

**30 minutes**

# June 22: The screen

After a long break for no reason, I am back to this project. I realized that the deadline is coming up, so I have to finish this.
Most of this project has been (sort of) simple up until this part for me. I want to be able to read my plugged in computers "now playing" window. Using this, I am, hopefully, going to display song title, artist, progress, and album cover. I think the easiest way to do this will be sung the winsdk python library. I used AI (I know I know, but I'll re-write it myself later) to generate some code that downloads the media thumbnail, shows the artist, progress, and song title. This worked (after some modification), and I think this proves that it will be possible to send the data serially to the display. I'm probably going to send the image and text to whatever microcontroller I use, and process it with [this TFT display repository](https://github.com/Bodmer/TFT_eSPI/tree/master) to show it. I think I might use a cheap ~1.5 in lcd [like this one that has a ST7789 chip and uses SPI](https://www.amazon.com/dp/B0C1TFWDS7) for the picture, and a little OLED for the text and stuff like [this](https://www.amazon.com/dp/B08CDN5PSJ) or [this](https://www.amazon.com/dp/B09T6SJBV5), which are both controlled over I2C. I am glad that I found solutions for this because I was worried I wouldn't be able to get this to work.

**1.5 hours**


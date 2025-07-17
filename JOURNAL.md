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

**0.5 hours**

# June 22/23: The screen

After a long break for no reason, I am back to this project. I realized that the deadline is coming up, so I have to finish this.
Most of this project has been (sort of) simple up until this part for me. I want to be able to read my plugged in computers "now playing" window. Using this, I am, hopefully, going to display song title, artist, progress, and album cover. I think the easiest way to do this will be sung the winsdk python library. I used AI (I know I know, but I'll re-write it myself later) to generate some code that downloads the media thumbnail, shows the artist, progress, and song title. This worked (after some modification), and I think this proves that it will be possible to send the data serially to the display. I'm probably going to send the image and text to whatever microcontroller I use, and process it with [this TFT display repository](https://github.com/Bodmer/TFT_eSPI/tree/master) to show it. I think I might use a cheap ~1.5 in lcd like [this one that has a ST7789 chip and uses SPI](https://www.amazon.com/dp/B0C1TFWDS7) for the picture, and a little OLED for the text and stuff like [this](https://www.amazon.com/dp/B08CDN5PSJ) or [this](https://www.amazon.com/dp/B09T6SJBV5), which are both controlled over I2C. I could also choose something like [this larger one](https://www.amazon.com/dp/B01CZL6QIQ) to display everything. I will probably control these using another Pi Pico so that the keyboard function doesn't break or slow down if this little screen does. I am glad that I found solutions for this because I was worried I wouldn't be able to get this to work.

![silly concept image](https://cdn-1.files.vc/files/bfy/a434fb8c9b481d74d2a532370e0f1221.png)


**1.75 hours**

# June 27: Nitty gritty

I looked at the displays again and I think I will use one display for the image and one for the text. I will probably use [this](https://www.amazon.com/dp/B0DN9NMBFW) for the image, and [this](https://www.amazon.com/dp/B0CFF17DGH?) for the text. I will control these from some RP2040 board and use [this library](https://learn.adafruit.com/adafruit-monochrome-1-12-in-128x128-oled/pinouts) for the text and [this one](https://github.com/adafruit/Adafruit-ST7735-Library) for the image. I think i will use another Pi pico. It took a little while to find documented displays in the right size that didn't cost a lot, but these seem fine.

**0.25 hours**

# July 15-16: Schematics again and board(!)

oops, i stalled!

![](https://hc-cdn.hel1.your-objectstorage.com/s/v3/d285198f39536ad42af8788581f7bb16e52c94f5_image.png)

For some reason I keep working late at night, so this writing may be sloppy.
I locked in and finished the schematic. I'm honestly not sure if I'm doing this right, and I'm probably using bad practices or something, but I think it _should_ work. I had to combine the schematic I made with the one I generated, but I'm not sure I did it right. It looks ok though, and I ended up using nets to connect them.

![](https://hc-cdn.hel1.your-objectstorage.com/s/v3/dfc141eb10033909b1c3710609c376a2d3b5aba2_image.png)

![](https://hc-cdn.hel1.your-objectstorage.com/s/v3/2ecfd2815a26ca843aa04b71708bd8212ed1a91f_image.png)

While looking at the connectors on the dislays I found this helpful review that I wanted to save for later 
> <sub><sup>"This TFT display looks great. I was able to very easily get it working with an Arduino Nano using some of the readily available Adafruit libraries. The only part that’s not well documented is that SCL (also called SCK) connects to D13, and SDA (also called MOSI) on D11 for the SPI hardware interface pins (on a Nano). Don’t confuse it with similarly/identically named I2C pins on A4 & A5 – this display uses an SPI connection, not I2C.  The fact that the silkscreen on the board is confusingly labeled with "SDA" and "SCL" could easily make you think it is I2C, which it's not.  It is bright and crisp, and I would gladly recommend it. You do need to solder the included header pins on yourself though. 5 stars."</sup></sub>

Wow, that formatting looks really weird. <sub><sup><sub><sup><sub><sup><sub><sup><sub><sup><sub><sup><sub><sup><sub><sup>hehehehehehehehehe</sup></sub></sup></sub></sup></sub></sup></sub></sup></sub></sup></sub></sup></sub></sup></sub>



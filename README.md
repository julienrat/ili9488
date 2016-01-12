# ili9488

Installation of aliexpress/alibaba/ebay 3,95 lcd screen (smartfriends) on Raspbian Jessie.

http://fr.aliexpress.com/item/3-95-Inch-LCD-Screen-For-Raspberry-Pi-B/32497237383.html?spm=2114.13010208.99999999.329.PP97UE

## sources
http://www.ittgroup.ee/et/ekraanid-ja-naidikud/626-lcd-tft-ekraan-395-480x320-raspberry-pi-le.html

https://github.com/notro/fbtft/issues/311

##modprobe 

###Test it !
```
sudo modprobe fbtft_device name=flexpfb rotate=180 fps=60 gpios=dc:18,reset:7,wr:17,cs:4,db00:22,db01:23,db02:24,db03:10,db04:25,db05:9,db06:11,db07:8

```
```
sudo modprobe flexfb width=480 height=320 buswidth=8 init=-1,0xb0,0x0,-1,0x11,-2,120,-1,0x3A,0x55,-1,0xC2,0x33,-1,0xC5,0x00,0x1E,0x80,-1,0x36,0x28,-1,0xB1,0xB0,-1,0xE0,0x00,0x04,0x0E,0x08,0x17,0x0A,0x40,0x79,0x4D,0x07,0x0E,0x0A,0x1A,0x1D,0x0F,-1,0xE1,0x00,0x1B,0x1F,0x02,0x10,0x05,0x32,0x34,0x43,0x02,0x0A,0x09,0x33,0x37,0x0F,-1,0x11,-1,0x29,-3
```
If it is correct, your screen will refresh.

```
con2fbmap 1 1
```
With this command you will be able to see startup messages.

###Make it permanent on jessie
Create and edit this file :
```
sudo nano /etc/modules-load.d/fbtft.conf
```
Put it this lines, and save (CTRL-X ; Y)
```
spi-bcm2835
fbtft_device
```
Create and edit this file to set fbtft_devices options :
```
sudo nano /etc/modprobe.d/fbtft.conf
```
Put it this line, and save (CTRL-X ; Y)
```
options fbtft_device name=flexpfb rotate=180 fps=60 gpios=dc:18,reset:7,wr:17,cs:4,db00:22,db01:23,db02:24,db03:10,db04:25,db05:9,db06:11,db07:8
```
Now do the same thing with flexfb :
```
sudo nano /etc/modules-load.d/flexfb.conf
```
Put it this lines, and save (CTRL-X ; Y)
```
flexfb
```
Create and edit this file to set flexfb options :
```
sudo nano /etc/modprobe.d/flexfb.conf
```
Put it this line, and save (CTRL-X ; Y)
```
options flexfb width=480 height=320 buswidth=8 init=-1,0xb0,0x0,-1,0x11,-2,120,-1,0x3A,0x55,-1,0xC2,0x33,-1,0xC5,0x00,0x1E,0x80,-1,0x36,0x28,-1,0xB1,0xB0,-1,0xE0,0x00,0x04,0x0E,0x08,0x17,0x0A,0x40,0x79,0x4D,0x07,0x0E,0x0A,0x1A,0x1D,0x0F,-1,0xE1,0x00,0x1B,0x1F,0x02,0x10,0x05,0x32,0x34,0x43,0x02,0x0A,0x09,0x33,0x37,0x0F,-1,0x11,-1,0x29,-3
```

# ili9488
## sources
http://www.ittgroup.ee/et/ekraanid-ja-naidikud/626-lcd-tft-ekraan-395-480x320-raspberry-pi-le.html

https://github.com/notro/fbtft/issues/311

##modprobe 

###Test it !

sudo modprobe fbtft_device name=flexpfb rotate=180 fps=60 gpios=dc:18,reset:7,wr:17,cs:4,db00:22,db01:23,db02:24,db03:10,db04:25,db05:9,db06:11,db07:8


sudo modprobe flexfb width=480 height=320 buswidth=8 init=-1,0xb0,0x0,-1,0x11,-2,120,-1,0x3A,0x55,-1,0xC2,0x33,-1,0xC5,0x00,0x1E,0x80,-1,0x36,0x28,-1,0xB1,0xB0,-1,0xE0,0x00,0x04,0x0E,0x08,0x17,0x0A,0x40,0x79,0x4D,0x07,0x0E,0x0A,0x1A,0x1D,0x0F,-1,0xE1,0x00,0x1B,0x1F,0x02,0x10,0x05,0x32,0x34,0x43,0x02,0x0A,0x09,0x33,0x37,0x0F,-1,0x11,-1,0x29,-3

###Make it permanent on jessie
Create and edit this file :

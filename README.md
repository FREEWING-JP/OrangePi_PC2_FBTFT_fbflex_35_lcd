# OrangePi_PC2_FBTFT_fbflex_35_lcd
Orange Pi PC 2 Allwinner H5 FBTFT fbflex 3.5 inch TFT LCD module SPI Control program

---
## Raspberry Pi用 FBTFT fbflex対応の汎用 3.5インチ TFT液晶を自前のプログラムで制御する方法
http://www.neko.ne.jp/~freewing/raspberry_pi/raspberry_pi_3_tft_lcd_35inch_fbflex_2/  

You can choose any control method .  
1. Linux spidev version  
2. [WIP] WiringPi library version  

## FREE WING Homepage
http://www.neko.ne.jp/~freewing/  

## Orange Pi PC 2 Homepage
http://www.orangepi.org/orangepipc2/  

## Allwinner H5 Homepage
http://www.allwinnertech.com/index.php?c=product&a=index&id=57  


---
## References（参考文献）
### KeDei 3.5 inch 480x320 TFT lcd from ali
https://www.raspberrypi.org/forums/viewtopic.php?p=1019562  
 by Conjur - Mon Aug 22, 2016 2:12 am - Final post on the KeDei v5.0 code.

### l0nley/kedei35
https://github.com/l0nley/kedei35

---
## Build Linux spidev version
##### # SPIdev - The Linux Kernel Archives
##### # https://www.kernel.org/doc/Documentation/spi/spidev

#### # Enable SPI
sudo nano /boot/armbianEnv.txt  
# Add Line  
overlays=spi1-spidev  

sudo reboot  

# ls -l /dev/spi*  
crw------- 1 root root 153, 0 Apr 15 12:54 /dev/spidev1.0  

#### # git clone
cd  
git clone https://github.com/FREEWING-JP/OrangePi_PC2_FBTFT_fbflex_35_lcd.git

#### # compile
cd ~/OrangePi_PC2_FBTFT_fbflex_35_lcd  
gcc -o fbflex_lcd_op_spidev fbflex_lcd_op_spidev.c  

#### # execute !
sudo ./fbflex_lcd_op_spidev  


---
## [WIP] Build WiringPi WiringOp H5 library version
##### # WiringPi - GPIO Interface library for the Raspberry Pi
##### # http://wiringpi.com/

#### # Enable SPI


#### # build WiringOp H5
cd  
git clone https://github.com/kazukioishi/WiringOP.git -b h5  
cd WiringOP  
chmod +x ./build  
sudo ./build  

#### # git clone
cd  
git clone https://github.com/FREEWING-JP/OrangePi_PC2_FBTFT_fbflex_35_lcd.git  

#### # compile
cd ~/OrangePi_PC2_FBTFT_fbflex_35_lcd  
gcc -o fbflex_lcd_op_wiringop fbflex_lcd_op_wiringop.c -lwiringPi  

#### # execute !
sudo ./fbflex_lcd_op_wiringop  


---
## Picture

![Raspberry Pi FBTFT fbflex 3.5 inch LCD module Control program](/fbtft_fbflex_35_lcd_1.jpg)

![Raspberry Pi FBTFT fbflex 3.5 inch LCD module](/fbtft_fbflex_35_lcd_2.jpg)


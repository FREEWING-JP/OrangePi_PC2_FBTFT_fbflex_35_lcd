# OrangePi_PC2_FBTFT_fbflex_35_lcd
Orange Pi PC 2 Allwinner H5 FBTFT fbflex 3.5 inch TFT LCD module SPI Control program

---
## Orange Pi PC 2で Raspberry Pi用 FBTFT fbflex対応の汎用 3.5インチ TFT液晶を自前のプログラムで制御する方法
http://www.neko.ne.jp/~freewing/raspberry_pi/orange_pi_pc2/  

You can choose any control method .  
1. Linux spidev version  
2. WiringOp H5(WiringPi) library version  

## FREE WING Homepage
http://www.neko.ne.jp/~freewing/  

## Orange Pi PC 2 Homepage
http://www.orangepi.org/orangepipc2/  

## Allwinner H5 Homepage
http://www.allwinnertech.com/index.php?c=product&a=index&id=57  

## Armbian - Orange Pi PC2
https://www.armbian.com/orange-pi-pc2/  

#### # Armbian Version
#### # uname -a
Linux orangepipc2 4.10.0-sun50iw2 #3 SMP Fri Apr 28 03:49:31 CEST 2017 aarch64 aarch64 aarch64 GNU/Linux  

---
## Other Resources

#### Orange Pi PC 2 Allwinner H5 FBTFT fbflex 3.5 inch TFT LCD module SPI Control program
https://github.com/FREEWING-JP/OrangePi_PC2_FBTFT_fbflex_35_lcd  

#### Raspberry Pi FBTFT fbflex 3.5 inch TFT LCD module SPI Control program
https://github.com/FREEWING-JP/RaspberryPi_FBTFT_fbflex_35_lcd  

#### Raspberry Pi KeDei 3.5 inch TFT LCD module V5.0 SPI Control program
https://github.com/FREEWING-JP/RaspberryPi_KeDei_35_lcd_v50  

#### tinydrm for KeDei 3.5 inch V5.0 LCD module
https://github.com/FREEWING-JP/tinydrm/tree/feature/kedei_35_v50/kedei_35_lcd_v50  

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

#### # Edit and Add Line
overlays=spi1-spidev  

sudo reboot  

#### # ls -l /dev/spi*
crw------- 1 root root 153, 0 Apr 29 08:16 /dev/spidev1.0  

#### # git clone
cd  
git clone https://github.com/FREEWING-JP/OrangePi_PC2_FBTFT_fbflex_35_lcd.git

#### # compile
cd ~/OrangePi_PC2_FBTFT_fbflex_35_lcd  
gcc -o fbflex_lcd_op_spidev fbflex_lcd_op_spidev.c  

#### # execute !
sudo ./fbflex_lcd_op_spidev  


---
## Build WiringPi WiringOp H5 library version
##### # WiringPi - GPIO Interface library for the Raspberry Pi
##### # http://wiringpi.com/

#### # Enable SPI
sudo nano /boot/armbianEnv.txt  

#### # Edit and Add Line
overlays=spi1-spidev  

#### # build WiringOp H5
cd  
git clone https://github.com/kazukioishi/WiringOP.git -b h5  
cd WiringOP  

#### # edit WiringOp H5
#### # nano wiringPi/wiringPiSPI.c
#### # const static char *spiDev1 = "/dev/spidev0.1" ; to "/dev/spidev1.0" ;
sed -i -e "s/spidev0\.1/spidev1\.0/g" wiringPi/wiringPiSPI.c

chmod +x ./build  
sudo ./build  

gpio readall  

#### # git clone
cd  
git clone https://github.com/FREEWING-JP/OrangePi_PC2_FBTFT_fbflex_35_lcd.git  

#### # compile
cd ~/OrangePi_PC2_FBTFT_fbflex_35_lcd  
gcc -o fbflex_lcd_op_wiringop fbflex_lcd_op_wiringop.c -lwiringPi -lpthread  

#### # execute !
sudo ./fbflex_lcd_op_wiringop  


---
## Picture

![Raspberry Pi FBTFT fbflex 3.5 inch LCD module Control program](/fbtft_fbflex_35_lcd_1.jpg)

![Raspberry Pi FBTFT fbflex 3.5 inch LCD module](/fbtft_fbflex_35_lcd_2.jpg)


"# OV7670_guide" 
# OV7670_guide
Yunxiang Zhang
University of Houston Clear Lake
3/21/2018

Hi,everyone. This project is a basic implementation of camera ov7670 on FPGA. I use this project as a case of study on my master thesis: Approximate Design. 
First of all, I want to thank Mr. Mike Field  <hamster@snap.net.nz>, our code here is mostly based on Mr. Field's code on http://www.hamsterworks.co.nz/mediawiki/index.php/Zedboard_OV7670. 
When I start this project, I find there have lots of example online but most example is based on Zedboard zynq-7000 or Terasic DE2-115 Development Board. Both of these development board have enough memory to save a 640x480 RGB image, but if we don't have that much memory, what should we do? I only get a Basys 3(Artix-7) on my hand, and the memory is just enought for a 320x240 RGB image. I notice in Mr. Field's code, he have a option to change resolution by push button, but it not work on my Basys 3. The reason I guess is because Basys 3 doesn't have enough memory to save a full image, but the ov7670 register set is to get 640x480 image, so the first part of image has replaced by the other part of image. By this reason, I make some changes on the register and finally make it work.
I have post most of the code for this project, but notice this design require 2 frequency of clock and memory block, I am highly not suggest you write your own pll(separate clock) code, try to use the IP core in Vivado to make life easier. PS: I try to write my own PLL, but on Artix-7 it doesn't work.
IP core:
Clocking wizard: 25hz and 50hz 
Block memory Generator: simple dual port ram, width 12 bit, Depth 76800(320x240)

# uc-xmake
Toolchain makefiles for a variety of microcontrollers

For me, a big part of the microcontroller learning process was to unravel the different build systems for different chips.  Usually this stuff is wrapped up behind an app, and glued to a bunch of other junk that obscures the big picture.  If you're into collecting throwaway chips on eBay, it's a big hike to get from datasheet to flashing your first blinky.  

The aim here is to build a generic __makefile__ construct that elucidates all of those intermediate steps.  So far, what we have is a __make__ construct for the STM32VLDiscovery cortex-M0 boards -- what it does is build all the relevant links to the Standard Peripheral Library and __openocd__ flash tools. 

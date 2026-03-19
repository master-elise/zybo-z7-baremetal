# Red Pitaya Zynq7010 (bare metal)

This repository is aimed to simplify the interaction with the Red Pitaya
Zynq 7010 by using standard Linux open source utilities (such as
gcc, gdb, openocd) instead of proprietary Xilinx SDK. It is something
like [libopencm3][3] but for Xilinx Zynq 7010.

## Quick Start

  1. Check if you have these apps installed:

     - `arm-none-eabi-gcc` (package name `gcc-arm-none-eabi` with Debian GNU/Linux)
     - `picolibc-arm-none-eabi` (Debian `arm-none-eabi-gcc` lost compatibility with 
`newlib` according to this 
[https://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg2084326.html][post])

  2. A `buildroot` image including `uboot` as found at https://github.com/trabucayre/redpitaya

  3. Open terminal and check for `/dev/ttyUSB0` when connecting the middle-USB microB port of
the Red Pitaya

  4. When prompted by uboot, hit a key to stop the countdown leading the booting Linux

  5. type the uboot commands
```
dcache off                                                                
fatload mmc 0 0x0 blink.bin                                          
dcache flush                                                              
go 0x0    
```
and the red LED should blink.

## Credits

Forked from https://github.com/3ap/zybo-z7-baremetal

  - `bsp/boot.S` & `bsp/Zynq.ld` from [bigbrett/zybo-baremetal][1]
  - `bsp/ps7_init_gpl.{c,h}` & `bsp/ps7_spl_init.c` from [Das U-boot][2]

[1]: https://github.com/bigbrett/zybo-baremetal
[2]: http://git.denx.de/?p=u-boot.git;a=summary
[3]: https://github.com/libopencm3/libopencm3

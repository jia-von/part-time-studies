# Raspberry Pi 4 Setup
This document will show the setup process for Raspberry Pi 4. Components included in this setup are:
- Raspberry Pi 4 8GB Model B with 1.5 GHz 64-bit quad-core ARMv8 CPU (8GB RAM).
- 32GB Samsung EVO+ Micro SD Card (Class 10) Pre-loaded with NOOBS.
- Raspberry Pi 4 Case with Integrated Fan Mount.
- Low Noise Bearing System Fan
- Micro HDMI Cable
- Set of Heat Sinks

## Setup
| Step 1 | Step 2 | Step 3 | Step 4 | 
| --- | --- | --- | --- |
| ![step1](photo\image5.jpeg) | ![step2](photo\image2.jpeg) | ![step3](photo\image0.jpeg) |  ![step4](photo\image6.jpeg) |
| Component available before the setup. | The Pi 4 board with heat sink attached to the Broadcom Cpu, LPDDR4 SDRAM, and USB 3.0 Controller. | Cooling fan with red and black wires to the GPIO header pins. | Completed setup with Pi 4 enclosed within the case. |

## NOOBS Installation
Raspberry Pi was the default NOOBS pre-loaded into the micro SD Card. I used [Raspberry Pi Imager](https://github.com/raspberrypi/documentation/blob/master/installation/sdxc_formatting.md) to format the SD card to the correct FAT file system. Method using [SD Formatter](https://www.sdcard.org/downloads/formatter/) tool did not show any success for this setup. 

I followed instructions from [*How to install Ubuntu Server on your Raspberry Pi*](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview) to install Ubuntu 20.04 LTS 64-bit server OS for arm64 architectures. I skip the Wi-Fi setup as I will be using an ethernet cable. I installed xubuntu with lightdm as the preferred desktop environment. 
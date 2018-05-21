* Raspberry PI 3
* Installation & First Steps


** Installation

a) Go to: https://etcher.io/
b) Install ETCHER in your system.
c) Download latest RASPBIAN version from: https://downloads.raspberrypi.org/raspbian_latest
d) Insert a 16GB SD Card and use Etcher to save Raspbian into SDCard.
d) Please, don't insert it on Rasberry, wait!!!

** Headless Setup

a) Eject and insert again the SD Card in your PC/Laptop (NOT IN RASPBERRY) and go to "Boot" SDCard's partition.
b) Edit "wpa_supplicant.conf" file you will find in this repository with your country, SSID and WPA Password of your WIFI Connection.
c) Copy "wpa_supplicant.conf" and "ssh" files you will find in this folder to "Boot" partition.
d) Eject the SDCard and insert it on a Raspberry PI 3.
e) Power ON and wait until Raspbian is installed and connected to WIFI.
f) From another system in the same WIFI network make ssh to this raspberry using "ssh pi@raspberrypi.local". Also you can check your router admin site  and check there raspberrypi assigned IP.


** How to check your IP

a) Using your WIFI Router admind site (normally 192.168.0.1 or 192.168.1.1, or similar - Google your ISP to get more info).
b) Using Adafruit's PIFinder app. You can download it here: https://github.com/adafruit/Adafruit-Pi-Finder/releases/tag/3.0.0

** Update your PI Software

a) Open a SSH connection (you can use PIFinder to do it, just press "SSH" bottom once it is found)
b) Do update and upgrade software (it may take some minutes) by typing:
'''
sudo apt-get update
sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y
sudo apt-get autoremove
'''
c) Set Raspberry PI parameters using raspi-config app:

'''
sudo raspi-config
'''

You should configure following items: 
- Set a new hostname, for example "iotServerHome" is a good one.
- Desktop/CLI Launch. For our purposes, CLI is better.
- Always ask for user password.
- Set Locales, keyboard, Time, etc.
- Expand the filesystem to SD.

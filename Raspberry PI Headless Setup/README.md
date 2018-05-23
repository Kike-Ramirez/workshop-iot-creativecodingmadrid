# Raspberry PI 3
# Installation & First Steps

## Installation

1. Go to: https://etcher.io/
2. Install ETCHER in your system.
3.  Download latest RASPBIAN version from: https://downloads.raspberrypi.org/raspbian_latest
4.  Insert a 16GB SD Card and use Etcher to save Raspbian into SDCard.
5.  Please, don't insert it on Rasberry, wait!!!

## Headless Setup

1. Eject and insert again the SD Card in your PC/Laptop (NOT IN RASPBERRY) and go to "Boot" SDCard's partition.
2. Edit "wpa_supplicant.conf" file you will find in this repository with your country, SSID and WPA Password of your WIFI Connection.
3. Copy "wpa_supplicant.conf" and "ssh" files you will find in this folder to "Boot" partition.
4. Eject the SDCard and insert it on a Raspberry PI 3.
5. Power ON and wait until Raspbian is installed and connected to WIFI.
6. From another system in the same WIFI network make ssh to this raspberry using "ssh pi@raspberrypi.local". Also you can check your router admin site  and check there raspberrypi assigned IP.


## How to check your IP

1. Using your WIFI Router admind site (normally 192.168.0.1 or 192.168.1.1, or similar - Google your ISP to get more info).
2. Using Adafruit's PIFinder app. You can download it here: https://github.com/adafruit/Adafruit-Pi-Finder/releases/tag/3.0.0

## Update your PI Software

1. Open a SSH connection (you can use PIFinder to do it, just press "SSH" bottom once it is found)
2. Do update and upgrade software (it may take some minutes) by typing:

`sudo apt-get update`
`sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y`
`sudo apt-get autoremove`

3. Set Raspberry PI parameters using raspi-config app:

`sudo raspi-config`

You should configure following items: 
* Set a new hostname, for example "iotServerHome" is a good one.
* Desktop/CLI Launch. For our purposes, CLI is better.
* Always ask for user password.
* Set Locales, keyboard, Time, etc.
* Expand the filesystem to SD.


# EXTRAS: Useful information for Raspberry setting

## Set Static IP

1. Open your terminal and open wpa_supplicant.conf file:

`sudo nano /etc/dhcpcd.conf'

![Open dhcpcd.conf](URL_TO_IMAGE)

Add following on sections:

* For Ethernet connection:

Go to following part of the file, uncomment and complete with your network parameters and your desired IP:

`# Example static IP configuration:`
`interface eth0`
`static ip_address=[DESIRED_IP_ADDRESS]/24`
`static routers=[IP_ROUTER]/24`
`static domain_name_servers=[IP_DNS] 8.8.8.8 fd51:42f8:caae:d92e::1`

* For WIFI connection:

In this case, you should define parameters for 'wlan0' interface.

`# Example static IP configuration:`
`interface wlan0`
`static ip_address=[DESIRED_IP_ADDRESS]/24`
`static routers=[IP_ROUTER]/24`
`static domain_name_servers=[IP_DNS] 8.8.8.8 fd51:42f8:caae:d92e::1`

* Your desired IP must be in your network range. You can check it using:
`ifconfig`

* To check your router IP:
`ifconfig`

* To check your DNS IP:
`nmcli dev show | grep DNS`

If not installed you must install:
`sudo apt-get install network-manager`



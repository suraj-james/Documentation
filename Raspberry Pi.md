# Raspberry Pi

## 1. Update your Sofware: 

Keeping your Raspberry Pi up-to-date

` sudo apt-get update` \
` sudo apt-get upgrade`\
` sudo reboot`

or

[Raspberry Pi Software Update Documentation](https://www.raspberrypi.org/documentation/raspbian/updating.md)


## 2. Set Screen Resolution to fit Full Screen
`sudo nano /boot/config.txt` \
Uncomment the `#disable_overscan=1` (Remove the #)

## 3. Change Keyboard Layout Configuration so that symbols like @,#,and " are mapped correct 
`sudo nano /etc/default/keyboard` \
Change `XKBLAYOUT="gb"` to `XKBLAYOUT="us"`

## 4. Install Airplay and make it enabled all the time
[Link](https://appcodelabs.com/7-easy-steps-to-apple-airplay-on-raspberry-pi) 
  1. Install Dependencies: \
`sudo apt-get install autoconf automake avahi-daemon build-essential git libasound2-dev libavahi-client-dev libconfig-dev libdaemon-dev libpopt-dev libssl-dev libtool xmltoman`
  2. Build & Install shairport-sync \
`git clone https://github.com/mikebrady/shairport-sync.git` \
		`cd shairport-sync` \
		`autoreconf -i -f` \
		`./configure --with-alsa --with-avahi --with-ssl=openssl --with-systemd --with-metadata` \
		`make` \
		`sudo make install` 
  3. Test Airplay to the Raspberry Pi \
		`sudo service shairport-sync start` \
		`sudo systemctl status shairport-sync.service` \
	  Note: Inorder to change the audio outout from hdmi to the 3.5mm audio jack 
	  ```
	  sudo raspi-config 
	  ->Advanced Options
	  ->Audio
	  ```
  4. Configure shairport-sync to Start Automatically \
		`sudo systemctl enable shairport-sync`

## 5. Enable Wifi to be on all the time to prevent wifi dropouts
`sudo nano /etc/network/interfaces` \
Go to the end of the file and add the lines:- 
``` 
# Disable wifi power management
wireless-power off
```
## 6. Enabling VNC (Virtual Network Computing)
VNC Connect from RealVNC is included with Raspbian by default. It consists of both VNC Server, which allows you to control your Raspberry Pi remotely, and VNC Viewer, which allows you to control desktop computers remotely from your Raspberry Pi should you want to. You must enable VNC Server before you can use it: 

To get the latest version of VNC Connect:
`sudo apt install realvnc-vnc-server realvnc-vnc-viewer`
Enabling VNC:
```
sudo raspi-config 
->Interfaces
```

## 7. Installing VLC Player

`sudo apt-get install vlc`

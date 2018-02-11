# rpi-hdmi-lcd-switcher

A script for Raspberry Pi to select either HDMI or LCD output at boot.

Original code by Hyell, sourced from: https://retropie.org.uk/forum/topic/4220/retropie-switches-between-lcd-hdmi/3 and https://retropie.org.uk/forum/topic/5527/raspberry-pi-official-lcd-screen-or-hdmi-option/2

This script checks for the presence of a HDMI display on system boot, then copies and pastes the correct config_hdmi.txt or config_lcd.txt file to /boot/config.txt and reboots the system.

If you have other config requirements make sure you add them to the config_lcd.txt and config_hdmi.txt files as required, as your config file will be overwritten and changes lost.

Instructions:

1. Create a new directory called /initDisplay in /home/pi and place initDisplay.sh inside it.

2. Save config_hdmi.txt and config_lcd.txt to /boot (don't forget to add any of your own config requirements).

3. Open /etc/profile.d/10-retropie.sh in a text editor and add the following to the top of the file:

#Check display config
/home/pi/initDisplay/initDisplay.sh

Now when you plug in an HDMI display and reboot, the script will run and change the config file before rebooting with the output to HDMI. Un-plugging the HDMI and rebooting will run the script again, rewriting the config file to output to LCD before rebooting with the output to LCD.

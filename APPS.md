# APPS for Maemo Leste

## What apps can I install?
In Maemo Leste you can install several types of applications:  
- <b>'Hildon' apps</b>. They are Debian Linux applications created by the Maemo Leste team on purpose to run on the Hildon desktop and Maemo Leste. When installed their icons appear inside the 'LESTE' icon.  
- <b>'Debian' apps</b>. They are Debian Linux applications created by any developer to run on multiple Debian-based operating system desktops (such as Ubuntu, Linux Mint or Debian itself). When they are installed their icons appear inside the 'DEBIAN' icon.  
- <b>'Webapps'</b>. They are applications that you can install through a browser like Chromium from different websites. When they are installed their icons appear within the 'WEBAPPS' icon.  

## How do I install 'Hildon' apps?
You can install them in the following ways:
- Through the Hildon Application Manager (it is already pre-installed).
- Through the terminal emulator (it is already pre-installed).
  - Search for the name of the app you want to install (for example NOMWeather) from this page: https://github.com/maemo-leste-extras
  - Open the terminal and run two commands:
    -     apt update -y
    -     apt install NOMWeather

## How do I install 'Debian' apps?
You can install them in the following ways:
- Through Synaptic App Manager (it is already pre-installed).
- Through the terminal emulator (it is already pre-installed).
  - Search for the name of the app you want to install searching in the web (they have to be based on ARM64 architecture)
  - Open the terminal and run two commands (example: libreoffice):
    -     apt update -y
    -     apt install libreoffice
- Downloading the application in a .deb file (for example 'sublimetext_arm64.deb' file in the ~/Downloads directory via Chromium) and running from the terminal:
    -     apt update -y
    -     cd ~/Downloads
    -     apt install ./sublimetext_arm64.deb

## List of my favorite applications for Maemo Leste.
My thinking for classifying them as 'favorites' is that they are easy to use for an average user and that they have a responsible design (they must be usable in both horizontal and vertical orientation, harmony in the design, appropriate menu size and buttons, etc.).  
From now on I am going to present a list of applications classified according to their function. Remember that to install them you just have to run "apt install name_of_app" from the terminal  
  - Text editors: mousepad

# Maemo Leste via proot for ARM64 Android 8+ devices.
## About Maemo Leste.
Maemo Leste is an open-source project aiming to maintain and continue the development of the Maemo platform, originally developed by Nokia for their mobile devices like the Nokia N900 smartphones.  
Maemo Leste focuses on providing an open and free software environment for mobile devices, emphasizing user freedom, privacy, and transparency. The project aims to extend the lifespan of devices like the Nokia N900, enabling users to use updated operating systems and retain control over their devices.  
Thanks to its members for this fantastic project. https://maemo-leste.github.io/  
You can say hello and join them on irc.libera.chat #maemo-leste  
If you do not want to install any application you can connect through https://web.libera.chat/  

## About Maemo Leste via proot.
I am an Android system user and I have had (and have) many Android smartphones. However, I still remember my beloved (now dead) Nokia N900 and its fantastic Linux Maemo Freemantle operating system. I remember how powerful I felt when this smartphone was my daily drive. I felt like I had a computer in my pocket with a Linux system and its infinite possibilities. Almost the same as with my computer (with Linux installed too).  
Unfortunately, the hardware of the Nokia N900 is very outdated compared to today's smartphones: little RAM, low-capacity battery, slow processor... And no manufacturer is considering resurrecting the Nokia N900 with current hardware. I am as much a lover of the Nokia N900 software as I am of the hardware of modern Android phones and if I have to choose I prefer the latter.  
This project arises from trying to combine the two things: having a modern mobile phone while being able to enjoy software derived from the one my beloved N900 had.
By installing Maemo Leste via proot you will not turn your modern Android smartphone into a smartphone with Linux installed natively, but you will be able to run Maemo Leste as another application and enjoy trying many apps as if you had a Nokia N900 again. Something is better than nothing :)  

## Tested on:
1. Samsung Galaxy Flip5 (Android 14). https://youtu.be/0rS_sP_NXAo
2. Blackberry Keyone (Android 8). https://youtu.be/1gHT4MTAo0g
3. Samsung Fold 1 F900F (Android 12).
4. Fxtec Pro1 (Android 10 via Lineage OS 17.1).
5. Hisense A5 (Android 9). 

## Requirements.
1. Android 8 or more based device.
2. Termux APK installed.  
3. Termux-X11 APK installed.  
4. Termux-api APK installed (optional, it should work on all devices).  
5. Termux:Widget APK installed (optional, see below).

## INSTALLING.
Following these steps you will install a modified Maemo Leste image with a minimum of installed apps that make it usable. From this base image you can install whatever you want:  
(WARNING: This Linux distro has access to your Android's internal storage (/sdcard). You could accidentally delete important files from your Android device. I am not responsible for any damages caused by installing or using this software. Use this software at your own risk.)  
- Download and install latest arm64-v8a APK release of Termux-x11 from https://github.com/termux/termux-x11/releases
- Configure this termux-x11 main preferences:
  - Display resolution mode: scaled
  - Display scale, % 160
  - Touchscreen input mode: Direct touch
      - "Direct touch" causes continuous Termux-X11 crashes. You can choose "Simulated touchscreen" option which does not cause crashes but is more annoying to use (it is a mix between mouse click and touchscreen tap, you will have to long tap to simulate the taps).
  - Show additional keyboard: disabled    
- Download and install latest APK file of Termux from https://f-droid.org/es/packages/com.termux/
- Open termux and run this (use copy & paste):
-     apt update -y && apt upgrade -y # press enter all times key if asked
-     termux-setup-storage # choose "allow"
-     apt install -y x11-repo && apt install -y nano wget termux-x11-nightly termux-api proot virglrenderer-android pulseaudio
-     wget -O ~/leste.tar.xz "https://www.dropbox.com/scl/fi/2v5k1epymb80yg5tkzl7t/maemoleste_proot_arm64_diejuse_v150.tar.xz?rlkey=ukeemrtphi5pwjt66dmrztv6q&dl=0"  # version 150
-     tar xJf leste.tar.xz -C ~
-     cp leste/diejuse_scripts/prootMaemo.sh .
- On Android 12+ Termux may be unstable. Android OS will kill any (phantom) processes greater than 32 (limit is for all apps combined) and also kill any processes using excessive CPU. You may get [Process completed (signal 9) - press Enter] message in the terminal without actually exiting the shell process yourself.
To solve, connect your Android device to your PC and run this ADB deactivation instrucions, on the following order:
    -      adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
    -      adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
    -      adb shell settings put global settings_enable_monitor_phantom_procs false
Source: https://maheshtechnicals.com/fix-termux-error-process-completed-signal-9-disable-phantom-process-killer-in-android-12-13/
### 

- OPTIONAL. If you want to access Android functions from Termux such as getting the battery level, opening the camera and other applications, follow next steps:
  - Download and install termux-api the latest apk release of Termux-api from https://f-droid.org/es/packages/com.termux.api/
  - Enable the advanced permission "Draw over other apps" of the Termux application (change it from Android settings).

## RUNNING IT.
1. Open termux-x11 app.
2. Open termux app. There only has to be one session running or the graphics acceleration provided by virglrender will not work.
3. Run:
    -      bash prootMaemo.sh
   Immediately open termux-x11 again.
   
## CLOSING IT PROPERLY.
1. Open termux app.
2. Press control+c.
3. Exit.
4. Long press on Termux and kill the session.  

### ADDING AN ICON TO OPEN MAEMO LESTE FROM YOUR ANDROID LAUNCHER.
1. Download and install the latest Termux:Widget APK from https://github.com/termux/termux-widget/releases
2. Open termux and run this commands:
-      [[ -d "mkdir ~/.shortcuts" ]] || mkdir ~/.shortcuts > /dev/null 2>&1 ; echo $'((sleep 8; am start -n com.termux.x11/.MainActivity)&)\nbash /data/data/com.termux/files/home/prootMaemo.sh' > ~/.shortcuts/startMaemo.sh ; chmod +x ~/.shortcuts/startMaemo.sh
3. Go to your home Android launcher, add a termux-widget and choose 'startMaemo.sh'.
4. Now Maemo Leste is just another application on your Android with its icon. Ready to launch.
5. You probably don't like the default icon that your Android launcher assigns to the widget. If you want to change the icon you will have to change to an Android launcher that allows it, such as Nova Launcher. You can download the Maemo Leste icon with this command (you will save the leste.png icon in /sdcard).
-      wget -O /sdcard/leste.png "https://raw.githubusercontent.com/diejuse/proot_MaemoLeste_on_Android/main/leste.png"

### VERSION UPDATES.
<a href='https://github.com/diejuse/proot_MaemoLeste_on_Android/blob/main/UPDATES.md'>Click here.</a>

### I WANT TO INSTALL APPS!
<a href='https://github.com/diejuse/proot_MaemoLeste_on_Android/blob/main/APPS'>Click here</a>

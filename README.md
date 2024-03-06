# Maemo Leste via proot for ARM64 Android 8+ devices.
WARNING: This Linux distro has access to your Android's internal storage (/sdcard). You could accidentally delete important files from your Android device. I am not responsible for any damages caused by installing or using this software/product. Use this software/product at your own risk.
## Tested on:
1. Samsung Galaxy Fold5 (Android 14).
2. Blackberry Keyone (Android 8).
3. Samsung Fold 1 F900F (Android 12).
## Requirements.
1. Android 8 or more based device.
2. Termux APK installed 
3. Termux-X11 APK installed.
4. Termux-api APK installed (optional, it doesn't wotk on all devices).
## INSTALLING.
- Download and install latest arm64-v8a APK release of Termux-x11 from https://github.com/termux/termux-x11/releases
- Configure this termux-x11 main preferences:
  - Display resolution mode: scaled
  - Display scale, % 160
  - Touchscreen input mode: Direct touch
  - Show additional keyboard: disabled    
- Download and install latest APK file of Termux from https://f-droid.org/es/packages/com.termux/
- Open termux and run this:
-     apt update -y && apt upgrade -y # press enter all times key if asked
-     termux-setup-storage # choose "allow"
-     apt install -y x11-repo && apt install -y nano wget termux-x11-nightly termux-api proot virglrenderer-android pulseaudio
-     wget -O ~/leste.tar.xz "https://www.dropbox.com/scl/fi/tl9q2lj4unp3p6b9dnip4/maemoleste_proot_arm64_diejuse_v100.tar.xz?rlkey=6z9ocfit00wl00fz17t9p5yge&dl=0"
-     tar xJf leste.tar.xz -C ~
-     cp leste/diejuse_scripts/prootMaemo.sh .
- On Android 12+ Termux may be unstable. Android OS will kill any (phantom) processes greater than 32 (limit is for all apps combined) and also kill any processes using excessive CPU. You may get [Process completed (signal 9) - press Enter] message in the terminal without actually exiting the shell process yourself.
To solve, connect your Android device to your PC and run this ADB deactivation instrucions, on the following order:
-      adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
-      adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
-      adb shell settings put global settings_enable_monitor_phantom_procs false
Source: https://maheshtechnicals.com/fix-termux-error-process-completed-signal-9-disable-phantom-process-killer-in-android-12-13/
### 
- (OPTIONAL. If you want to access Android functions from Termux such as getting the battery level, opening the camera and other applications. Does not work on all devices.) Download and install termux-api the latest apk release of Termux-api from https://f-droid.org/es/packages/com.termux.api/ 
## RUNNING
1. Open termux-x11 app.
2. Open termux app. There only has to be one session running or the graphics acceleration provided by virglrender will not work.
3. bash prootMaemo.sh. Immediately open termux-x11 again.
## CLOSING PROPERLY.
1. Open termux app.
2. Press control+c.
3. Exit.
4. Long press on Termux and kill the session.


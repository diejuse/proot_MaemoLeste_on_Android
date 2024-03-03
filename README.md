# Maemo Leste via proot for ARM64 Android 8+ devices.
## Tested on:
1. Samsung Galaxy Fold5 (Android 14).
2. Blackberry Keyone (Android 8)
## Requirements.
1. Android 8 or more based device.
2. Termux installed 
3. Termux-X11 installed.
## Steps to install.
### Install termux and termux-11
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
-     apt install -y x11-repo && apt install -y nano wget termux-x11-nightly proot virglrenderer-android pulseaudio
-     wget -O ~/leste.tar.xz https://www.dropbox.com/scl/fi/ar3k139psregx763dlpc4/maemoleste_proot_arm64_diejuse_v1.tar.xz?rlkey=k47q3oc7wibcez1okrj6xvt08
-     tar xJf leste.tar.xz -C ~
-     cp leste/diejuse_scripts/prootMaemo.sh .
- On Android 12+ Termux may be unstable. Android OS will kill any (phantom) processes greater than 32 (limit is for all apps combined) and also kill any processes using excessive CPU. You may get [Process completed (signal 9) - press Enter] message in the terminal without actually exiting the shell process yourself.
To solve, connect your Android device to your PC and run this ADB deactivation instrucions, on the following order:
-      adb shell "/system/bin/device_config set_sync_disabled_for_tests persistent"
-      adb shell "/system/bin/device_config put activity_manager max_phantom_processes 2147483647"
-      adb shell settings put global settings_enable_monitor_phantom_procs false
-  



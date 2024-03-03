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
-     apt install -y x11-repo && apt install -y termux-x11-nightly virglrenderer-android pulseaudio
-     wget -O ~/leste.tar.xz https://www.dropbox.com/scl/fi/ar3k139psregx763dlpc4/maemoleste_proot_arm64_diejuse_v1.tar.xz?rlkey=k47q3oc7wibcez1okrj6xvt08


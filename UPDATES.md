## Version 100 (06/03/2024)
The base version (Chimaera Devuan). Based on ARM64 generic Raspberry Pi 3 https://maedevu.maemo.org/images/arm64-generic/20200114/

## Version 110 (14/03/2024)
List of fixes:
- "sudo"  
  It is now possible to use Maemo Leste like "user" (not root user). For example, being able to do "sudo apt update". To change from "root" to "user", from the terminal: "su - user" and "exit" to go back to root.
- “Closed error: The permission of the setuid helper is not correct” error fixed.  
- Opening the Android applications of Whatsapp, Camera, Call, Messages, Settings and the battery level widget now works on all mobile phones. You need to have Termux-api apk installed and enable the advanced permission "Draw over other apps" of the Termux application (change it from Android settings).  
- Dummy network fixed. Hildon app manager (HAM) now works.  
  => Thanks to the investigations of the Maemo Leste member @arno11  
- Several files have been modified such as:  
  - /diejuse_scripts/prootMaemo.sh  
  - /diejuse_scripts/launchMaemo.sh  
  - /etc/osso-af-init/af-defines.sh  
  - /etc/apt/sources.list  
  - /etc/apt/sources.list.d/hildon-applications-manager.list  
  - ~/.bashrc
  - /diejuse_scripts/android    # NEW
  - /diejuse_scripts/android_xxxxx.sh
## Version 120 (16/03/2024)  
List of fixes:  
- Maemo Browser ('jid' package) running.  
- Fixed some bugs in the prootMaemo.sh script. Now launching Android applications from Maemo Leste works on more devices (tested on Fxtec Pro 1 with Lineage OS 14). 
- Fixed '"dpkg:warning files list file for package 'xxxx' missing; assuming package has no files currently installed"  multiple errors when 'apt' command is used from terminal.  
- 'dialog' package installed to avoid "debconf: falling back to frontend readline" annoying message when 'apt' is used.  
- Installed 'pidgin' and 'purple-telegram' so that a Maemo lLeste user can send and receive messages via telegram, irc, xmpp and other protocols.  
## Version 150 (03/04/2024)  
- 'Diejuse_onboard' rebuilded and improved.
- Some fixes in 'prootMaemo.sh'.
- New Debian apps installed: 'gdebi', 'drawing'.
- New Maemo Leste apps installed: 'modest' (email client), 'easylist'.
- 'mousepad' text editor uninstalled, 'gedit' installed instead.

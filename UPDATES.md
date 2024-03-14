## Version 100.
The base version.
## Version 101. 14/03/2014.
List of fixes:
- sudo
  It is now possible to use Maemo Leste like "user" (not root user). For example, being able to do "sudo apt update". To change from "root" to "user", from the terminal: "su - user" and "exit" to go back to root.
- “Closed error: The permission of the setuid helper is not correct” error fixed.
- Opening the Android applications of Whatsapp, Camera, Call, Messages, Settings and the battery level widget now works on all mobile phones.
- Dummy network fixed. Hildon app manager (HAM) now works.
  => Thanks to the investigations of the Maemo Leste member @arno11
- Several files have been modified such as:
  - /diejuse_scripts/prootMaemo.sh
  - /diejuse_scripts/launchMaemo.sh
  - /etc/osso-af-init/af-defines.sh
  - /etc/apt/sources.list
  - /etc/apt/sources.list.d/hildon-applications-manager.list
  - ~/.bashrc
  - /diejuse_scripts/android_xxxxx.sh
 

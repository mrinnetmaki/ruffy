Forked the repo.
Downloaded the repo.
- Good to see some code before working on it, try compiling and installing it to the device I have, although I knew I needed to change the OS to get the app to actually work with the pump.

Opened the project in Android Studio (I had a version already installed).
- Gradle 'ruffy' project refresh failed
- Failed to find target with hash string 'android-25' in: ...
- Install missing platform(s) and sync project

Clicked the prompt and let Android Studio's Component Installer work it's magic.
- Compiled successfully.

Tried running on device
- USB cable in, unlock device
- Run in Android Studio
- Seems to work fine, but nothing happens on the phone
- Works, when launched from the app icon in the menu. Wrong/no default activity?

Prepared the pump
- as instructed by the app
- App: Starting rfcomm to wait for Pump connection
- Pump: no device found

Update the phone
- required, as there's a bug in Android bluetooth from 4.2 until the latest versions
- versions older than 4.2 work OK, I've heard
- an alternative is to use LineageOS
- my phone is MotoG 2, so I find my setup instructions at https://wiki.lineageos.org/devices/thea/install


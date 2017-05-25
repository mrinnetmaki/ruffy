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

- run `adb devices` (get "List of devices attached / DEVICE_ID	device" as response)
- run `adb reboot bootloader` (device goes to boot menu)
- run `fastboot devices` (get DEVICE_ID	fastboot as response)
- run 'fastboot oem device-info' as instructed (bit worrying, got:
(bootloader) slot-count: not found
(bootloader) slot-suffixes: not found
(bootloader) slot-suffixes: not found
...
(bootloader) 'device-info' is not a supported oem command
(bootloader) See 'fastboot oem help'

FAILED (remote failure)
finished. total time: 0.017s

Start to unlock the device
- Go to http://motorola-global-portal.custhelp.com/app/standalone/bootloader/unlock-your-device-a
- Accept
- Enter Motorola ID (ask for a password reset link)
- Sign in with Google
- Get to unlock instructions screen
- Assume I have the drivers installed

...
(bootloader) XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
(bootloader) XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
(bootloader) XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
(bootloader) XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
(bootloader) XXXXX
OKAY [  0.176s]
finished. total time: 0.176s

- Edit to a combined string.
- Paste to input on Motorola page. Unlocks the form. Great!

Got the email, with the unique ID string.
- fastboot oem unlock UNIQUE_STRING
(bootloader) slot-count: not found
(bootloader) slot-suffixes: not found
(bootloader) slot-suffixes: not found
...
(bootloader) Check 'Allow OEM Unlock' in Developer Options.
FAILED (remote failure)
finished. total time: 0.046s

Right. :(

Volume UP, for normal booting.

- Access {} Developer options menu (don't remember how that was enabled) ( go into Settings -> About and find the Build Number and tap on it 7 times to enable developer settings)
- Select OEM unlocking
- Enter device PIN

Accept the warning (Device protection features are not enabled when this setting is turned on)

- Run `adb reboot bootloader`
- Run fastboot oem unlock UNIQUE_STRING
(bootloader) slot-count: not found
(bootloader) slot-suffixes: not found
(bootloader) slot-suffixes: not found
...
(bootloader) Unlock code = UNIQUE_STRING

(bootloader) Phone is unlocked successfully!
OKAY [  1.338s]
finished. total time: 1.338s


fastboot flash recovery twrp-3.1.1-0-thea.img 
(bootloader) slot-count: not found
(bootloader) slot-suffixes: not found
(bootloader) slot-suffixes: not found
(bootloader) has-slot:recovery: not found
target reported max download size of 536870912 bytes
sending 'recovery' (7926 KB)...
OKAY [  0.300s]
writing 'recovery'...
OKAY [  0.334s]
finished. total time: 0.634s

(plenty of going back and forth, not always clear...)

Finally got LineageOS installed and booting!

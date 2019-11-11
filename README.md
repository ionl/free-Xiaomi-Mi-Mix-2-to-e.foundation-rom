### Device : Xiaomi Mi Mix 2
* Before : Android 9 MIUI Global 10.4.1
* After : /e/ Android 8.1.0 : https://e.foundation/

#### [Thanks to androidinfotech](https://www.androidinfotech.com/root-xiaomi-mi-mix-2-oreo/)
---
> __Very important: please read the following carefully before proceeding!__

Installing a new operating system on a mobile device can potentially

    1. lead to all data destruction on the device
    2. make it an unrecoverable brick.

> So please only flash your device if you know what you are doing and are OK with taking the associated risk.
I deny any and all responsibility about the consequences of using /e/ software and/or /e/ services.
---
1. __Start configuration__
    * Backup your current files and data
    * Make sure your device battery is charged above 50%
    * `Settings > About phone`, enable
        * Developer Options (Tap on the MIUI version 7 times)
    * `Settings > SYSTEM SETTINGS > Additional settings > Developer Options`, enable
        * OEM unlocking
        * USB Debugging
        * Mi Unlock Status
            * Give permission
            * Add mi account
2. __Unlock bootloader__
    * On PC Windows, go to https://en.miui.com/unlock/
    * Log to mi account and download `Mi Unlock`
    * Shut down your phone. Hold volume down key and power button to enter `Fastboot mode`
    * Connect your phone to PC using USB cable and click `miflash_unlock.exe`
3. __Replace recovery : TWRP__
    * Install ADB drivers
    * Shut down your phone and connect phone to pc
    * Enter `Fastboot mode` (hold volume down key and power button)
    * Check usb link<sup>2</sup>
        * $ fastboot devices -l
            > 6bb90eca fastboot usb:1-1.2
        * $ fastboot flash recovery [recovery.img](recovery.img)
        * $ fastboot boot [recovery.img](recovery.img)
        * $ adb devices
            > List of devices attached
               6bb90eca recovery
    * Transfer zip
        * $ adb push [Disable Force Encryption](DisableForceEncryption_Treble.zip)<sup>3</sup> /sdcard
        * $ adb push [Magisk](Magisk-v20.0.zip)<sup>4</sup> /sdcard
    * Install zip with `TWRP > Home  > Install > Select`
4. __Install /e/__
    * Download [/e/ rom](http://ionl.fr/chiron.zip)<sup>5</sup>
    * `TWRP > Home > Advanced > ADB Sideload`, then swipe to begin sideload.
    * On the host machine, sideload the package using
        * $ adb sideload [chiron.zip](chiron.zip)
    * Once finished, `TWRP > Home > Reboot > System`
---
<sup>1</sup> https://eu.dl.twrp.me/chiron/twrp-3.3.1-1-chiron.img.html

<sup>2</sup> adb usb link help
* $ lsusb
    > Bus 002 Device 009: ID 18d1:d00d Google Inc.
    vendor id: 18d1
    product id: d00d
* $ sudo vim /etc/udev/rules.d/51-android.rules
>    only fasboot menu
* $ sudo udevadm control --reload-rules
* $ sudo usermod -aG adbusers $LOGNAME
* $ sudo adb kill-server
* $ sudo adb start-server

<sup>3</sup> https://www.cyanogenmods.org/downloads/disable-force-encryption-twrp-flashable-zip-treble/

<sup>4</sup> https://github.com/topjohnwu/Magisk/releases/

<sup>5</sup> This rom has been modified because of error when flashing
>
    assert failed : xiaomi.verify_trustzone("TZ.BF.4.0.6-00124","TZ.BF.4.0.6-00130") == "1"

> solution
* Unzippe [/e/ rom](https://doc.e.foundation/devices/chiron/install)
* Delete 2nd line from file `META-INF/com/google/android/updater-script`
* Zipped it and push it to http://ionl.fr/chiron.zip

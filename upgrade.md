> Xiaomi Mi Mix 2

## Before flash firmware

* Android version  : 8.1.0
* v.security patch : 2018-06-01
* security patch   : 2020-02-05
* Baseband version : AT20-0718_1855_85ac818
* kernel version   : 4.4.78

## [/e/ foundation documentation](https://doc.e.foundation/devices/chiron/)

> on your computer

## upgrade firmware miui (unofficial)

> [/e/ foundation forum](https://community.e.foundation/t/unofficial-build-xiaomi-mi-mix-2-chiron/8667)

* download [global stable rom pie 10.4.2](https://bigota.d.miui.com/V10.4.2.0.PDEMIXM/miui_MIMIX2Global_V10.4.2.0.PDEMIXM_3338a674f3_9.0.zip)
*

## install /e/

> 2020-03-31 : MIUI firmware version 9.5.16 or newer

* download [rom and sha256](https://images.ecloud.global/dev/chiron/)
* check validity `$ sha256sum -c xxx.zip.sha256sum`
* unzip
* update file `META-INF/com/google/android/updater-script`
* zip
* move it on smartphone
* reboot smartphone into recovery. Turn off Mi Mix 2 (press and hold it with with volume up key)
* install rom

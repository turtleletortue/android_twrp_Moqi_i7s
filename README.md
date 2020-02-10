# device_realme_RMX1921
Device Tree for Realme XT
@@ -24,61 +24,3 @@ The Realme XT (codenamed _"RMX1921"_) is a mid-range smartphone from Realme. It
## Device Picture

![Realme XT](https://fdn2.gsmarena.com/vv/pics/realme/realme-xt.jpg "Realme XT")

# android_device_xiaomi_RMX1921
For building TWRP for Realme XT

TWRP device tree for Realme XT

## Features

Everything works
Android 10 blobs
Stock 10 kernel
Uses the twrp theme to blackout notch area, Thanks to @mauronofrio

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_omni.git -b twrp-9.0
repo sync
```

Then add these projects to .repo/local_manifests/roomservice.xml:

```xml
<project path="device/realme/RMX1921" name="pjgowtham/android_device_realme_RMX1851" remote="github" revision="android-9.0" />
<remove-project name="android_bootable_recovery"
<project path="bootable/recovery" name="mauronofrio/android_bootable_recovery" remote="github" revision="android-9.0" />
```

Finally execute these:

```
. build/envsetup.sh
lunch omni_RMX1921-eng
mka recoveryimage ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
```

To test it:

```
fastboot flash recovery out/target/product/RMX1921/recovery.img
```

## Other Sources

Kernel Sources: using precompiled stock kernel

## Thanks

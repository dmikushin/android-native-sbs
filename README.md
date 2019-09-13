# Android Native SBS

Android application to switch display into side-by-side VR mode written by Fredrik Markström.
You can see it in action below:

[![](http://img.youtube.com/vi/74F7AbyVFl0/0.jpg)](http://www.youtube.com/watch?v=74F7AbyVFl0)

This is the source code for the installation and control app for the first version of
Native SBS support for Android. Native SBS makes it possible to use all apps (like Plex,
Play Movies, Netflix, etc.) with opendive, google cardboard or similar for viewing on a large
virtual screen.

## Prerequisites

- Android phone with root access
- A working recovery in case something goes horribly wrong
- For building from source gradle is needed, e.g.: `sudo apt install gradle`

## Building

```
git clone https://github.com/dmikushin/android-native-sbs.git
cd android-native-sbs
gradle
```

## Troubleshooting

The code that is the core of this functionality is not part of any open API so the compatibility
of this app needs to be tested on a per android version and device type.

When you have installed and enabled SBS (in the app) your device might fail to boot. If you
selected the option of only enable "on next boot" you can just power off and power on the phone
again and it *should* boot fine. If you select the "Dangerous" option you might not be so lucky.

If your device fails to boot, read the "Uninstall manually" chapter below.

- This has only been tested on AOKP_jflte_kitkat_nightly_2014-05-24 (AOKP based on 4.4.2 on Samsung
  S4 - I9505), but probably works with all CM11 based KitKat roms. (And possibly some KitKat stock
  ROMs)
- If the phone hangs, reboot it.
- I use it with a bluetooth mouse and have watched hours and hours of movies with it (mostly when flying).

## Uninstall manually

To manually undo everything SBS has done to your device

1) Boot into recovery and connect to your phone with adb
2) Mount /system read/write

```
mount -o rw /system
```

3) Restore /system binaries

```
mv /system/bin/surfaceflinger.real /system/bin/surfaceflinger
```

4) Unmount /system again
   
```
umount /system
```
   
5) Reboot phone

```   
reboot
```

## Further Work

I1) Enable/disable in a way that works in both SBS and non-sbs mode. Since using the touch-screen is hard in SBS mode.
I2) Lens distortion correction (any opengl-wizards out there that would like to help ?)
I3) Incorporate the change in some open source ROMS (the patch is quite small and isolated but does need some work)
I4) Add permanent installation option.
I5) Make individual zoom settings for landscape and portrait mode.
I6) Make zoom settings persistent

## Contributions

I have a lot of projects, a day-job and not much time for this project, in addition estetics and user interfaces aren't my 
strong side. So if someone wants to help rewrite this into something neater I'd appreciate the help.


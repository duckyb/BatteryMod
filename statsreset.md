[Home](/index.md)   >   [Tips & Tricks](/statsreset.md)

# Calibrating your new battery
To calibrate your battery, simply discharge your phone to 0% (until it shuts off), then charge it to 100% without turning it on.
Repeat this step one or two times and everything should work.

To know if your battery is calibrated correctly, try using [AccuBattery](https://play.google.com/store/apps/details?id=com.digibites.accubattery), after some charge cycles it will display a calculated capacity. This number should be around 3600mAh or more: <br/>

<img src="img/accubattery.jpg" height="50%" width="50%"/>

# Forcing a reset of the battery stats
## Method 1 (root explorer):
1. Delete the file located in `data/system/batterystats.bin` <br/>
2. Let your device discharge to 0% (until it shuts off)
3. Charge it to 100%

> The `batterystats.bin` file only contains the information that is displayed in `Settings > Battery`, for this reason deleting it might not be helpful. ([Source](https://www.xda-developers.com/google-engineer-debunks-myth-wiping-battery-stats-does-not-improve-battery-life/))

## Method 2.1 (aka Terminal):
1. Open [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en)
2. Type: <br/>
  `su` <br/>
  `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` <br/>
  Nothing should happen inside the terminal window, but your stats should have been reset.

### Method 2.2 (aka Lukas0610's Method):
1. Discharge down to ~5%.
2. Open [Terminal Emulator](https://play.google.com/store/apps/details?id=jackpal.androidterm&hl=en)
3. Run `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` (Resets the fuelgauge) <br/>
        Nothing should happen inside the terminal window, but your stats should have been reset.
4. Charge to 100%
5. Run `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` <br/>
        Nothing should happen inside the terminal window, but your stats should have been reset. <br/>
Repeat all steps 2-3 times!

## Method 3 (aka Hard Stats Reset):
This method is useful for when the previous methods don't seem to work.
1. Let your device discharge to 0% (until it shuts off)
2. Switch on once more to make sure battery really is 0% (it should then immediately switch off again)
3. Now, **keep the device off**, plug in the charger and let it charge to 100%
4. When battery is full, switch the phone on, unplug and check if the batter immediately drops 1 or 2 %
5. If the battery immediately drops, plug in the charger once more (while the device is ON) and let it charge completely
6. Once fully charged, don't plug out your charger, open root explorer, at the top just click `mount R/O`, then it will set as _mounted as R/O_.
7. Navigate to `Data/System/batterystats.bin`
8. Tap the `batterystats.bin` file and it will show the file option, select `delete`.
9. Once it done, close the root explorer and use the phone as usual until it switches itself off (battery empty).
10. **Do not charge your phone if the battery is not completely empty**.
11. Charge your phone while powered as usual until it shows 100% charge.
12. Make sure that during discharging you don't reboot your phone! Or else the system will create a new `batterystats.bin` file or if already made, it will get corrupted and you will have to start again from first step!
13. Repeat steps 11 and 12 until the battery behaves normally.

# Fix device forgetting Wifi networks / Bluetooth broken

1. With any `build.prop` editor or your root file manager edit your `build.prop` and set `ro.securestorage.support = false`.
2. Save `build.prop` and download fix zip file to sd card. (use `#fixwifi` command in the telegram chatroom)
3. Reboot in recovery mode and flash that zip file.
4. Reboot system

# Fixing the gap on your back cover

The Galaxy S7edge batteries usually are 1 millimiter thicker than stock batteries, but it's possible that some arrive thinner than others. If your battery isn't very thin, you will need to use this method to fix the little gap between the back cover and the phone.

[Picture of the 5 screws](https://i.imgur.com/cB60Lku.jpg)

Open up your phone and turn these screws counter-clockwise. You will see that where you unscrew them, the screen will move away from the body of the phone, this way it will make more space for the back cover. Of course you don't have to make a gap behind the screen, you just need to find the right distance of the screws so that the back cover fits well without separating the screen.

[Picture of the fixed gap](https://i.imgur.com/2RzlxEv.jpg)

# Removing extra bloatware from any device (by /u/dosangst)

<img src="img/adbshell.png"/>

1. Install USB drivers for your [Device](https://developer.android.com/studio/run/oem-usb.html)
2. [Download](http://lifehacker.com/the-easiest-way-to-install-androids-adb-and-fastboot-to-1586992378) and Install ADB tools
3. Enable[ Developer Options](http://wccftech.com/enable-developer-options-android-nougat/) and [USB Debugging](https://technosamigos.com/enable-usb-debugging-on-android-nougat-phones/)
4. Find a good USB cable, plug it into your computer and then to your device. When the pop-up appears asking you to authorize the device, allow it. 
5. Open a command prompt (cmd in windows) and type: <br/>
        `adb devices`
6. This should return the ID of your device. If not, please go back and retrace your steps.
7.  Use the following commands to find the apps you want to disable <br/>
        `adb shell pm list packages`
8. Now type: <br/>
        `adb shell`
9. This should give you a new prompt, something to the effect of (device-model):/ - here type the following:  <br/>
        `pm uninstall -k --user 0 <name of package>`
This should return 'Success' at which point the package has been removed! <br/>

This has been tried on about half a dozen devices and it works on every single one, including the LG G6, Samsung S8, Google Pixel (Removed System Applications!)

# Making fingerprint sensor faster

If you have registered multiple fingers on the sensor, try removing all saved fingerprints, then register just ONE fingerprint, but use all the fingers you want while registering. For example, if you want to register 4 fingers (both index and thumbs), register 0-25% with 1 finger, 25-50% with another, 50-75% with another and 75-100% with last finger.

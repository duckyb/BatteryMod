# Calibrating your new battery
To calibrate your battery, simply discharge your phone to 0% (until it shuts off), then charge it to 100% without turning it on.
Repeat this step one or two times and everything should work.

# Forcing a reset of the battery stats
## Method 1 (root explorer):
1. Delete the file located in `data/system/batterystats.bin` <br/>
2. Let your device discharge to 0% (until it shuts off)
3. Charge it to 100%

## Method 2 (terminal):
1. Open Terminal Emulator
2. Type: <br/>
  `su` <br/>
  `echo 1 > /sys/class/power_supply/battery/batt_reset_soc` <br/>

Nothing should happen inside the terminal window, but your stats should have been reset.

## Method 3 (HARD STATS RESET):
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

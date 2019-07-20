
# How to downgrade bose QC35 ii firmware

I success downgrade QC35II from 4.5.2 to 2.5.1.1182,and the decice work well, for ANC, it's hard to say.
```
7/19/2019 23:19:24.701, Error, Expecting version to be 4.5.2.144, read 2.5.1.1182
7/19/2019 23:19:24.701, Info, Update: Waiting for external bootmode reset -> Error state
7/19/2019 23:19:29.763, Info, Internal version is 2.5.1.1182
7/19/2019 23:19:29.763, Info, External version is 2.5.1.1182
7/19/2019 23:19:29.763, Info, Device version is 2.5.1.1182
```

but, i don't recommand to do it, high risk!!!!!!!!!!!!!! high risk, and high risk.

For windows:

When do updating, it will download the firmware to:
```
C:\Users\<username>\AppData\Local\Temp
```
There are three files, something like:
```
Bose Updater.fl7980 33KB
Bose Updater.Nl7980 22089KB
Bose Updater.Ya7980 1897KB
```
Comparing these files by Beyond Compare 4 bytes by bytes.I find actully they are the 100% same files:
```
BayWolf_4.5.2_acorn_coeffs_signed.xuv 33KB
BayWolf_4.5.2_ext_signed.xuv 22089KB
BayWolf_4.5.2_stack_plus_app.dfu 1897KB
```
From the update log:
```
7/19/2019 23:13:51.661, Info, Update: Idle -> Downloading firmware
7/19/2019 23:13:53.846, Info, Done downloading https://downloads.bose.com/ced/baywolf/BayWolf_4.5.2_acorn_coeffs_signed.xuv (result NoError) (time 2)
7/19/2019 23:13:56.003, Info, Done downloading https://downloads.bose.com/ced/baywolf/BayWolf_4.5.2_stack_plus_app.dfu (result NoError) (time 4)
7/19/2019 23:14:01.714, Info, DIAGNOSTICS: Rate = 484528 B/s; Time = 50 sec.
7/19/2019 23:14:47.912, Info, Done downloading https://downloads.bose.com/ced/baywolf/BayWolf_4.5.2_ext_signed.xuv (result NoError) (time 56)
7/19/2019 23:14:49.799, Info, DOWNLOADING_FIRMWARE - DONE
7/19/2019 23:14:49.799, Info, Enter Internal Bootmode
7/19/2019 23:14:49.799, Info, Update: Downloading firmware -> Waiting for internal bootmode
7/19/2019 23:14:49.800, Info, reset-enter-internal-bootmode
7/19/2019 23:14:49.805, Info, Num excluded devices = 0
7/19/2019 23:14:49.807, Info, Waiting for device to drop out...(0x40fe)
7/19/2019 23:14:50.806, Info, Device has disconnected
7/19/2019 23:14:52.844, Info, waitForReset: Device is reset
7/19/2019 23:14:52.854, Info, waitForReset: Wait for device startup
7/19/2019 23:14:57.870, Info, 1 BOSE CONNECTED DEVICE(S) WITH VID 0x05A7
7/19/2019 23:14:57.870, Info, 1 \?\hid#vid_05a7&pid_4020#7&2cddf5a5&0&0000#{4d1e55b2-f16f-11cf-88cb-001111000030}
7/19/2019 23:14:57.972, Info, DeviceConnectionManager::doUpdate - DONE SUCCESS
7/19/2019 23:14:58.917, Info, Update: Waiting for internal bootmode -> Internal bootmode updating
7/19/2019 23:14:58.918, Info, HidDfuFlasher: Validating input file
7/19/2019 23:14:58.943, Info, Data to write {1894960}
7/19/2019 23:14:58.949, Info, Downloading firmware to device...
7/19/2019 23:16:06.480, Info, DoUpgrade: Data left to write {0}
7/19/2019 23:16:06.480, Info, DoUpgrade: retVal {0}
```
We can find, after finishing download image from the internet, it will reboot the devices to reset it. So the device will disconnect to PC. And when the device disconnect, there is a notification sound from windows.

So, If we hear such notification sound, copy the old firmware files to 
```
C:\Users\<username>\AppData\Local\Temp 
```
to cheat updater, then it will download the old firmware files to device and update.


# Way of downgrade BOSE QC35 ii firmware

Environment: Bose Updater ver is 6.0.0.4388, win7, chrome 75.0.3770.142

1.Go to http://btu.bose.com/ , enter "a","d","v","up","down"

2.Click update button.

3.Check the name of the three firmware files in 
```
C:\Users\<username>\AppData\Local\Temp 
```
They are looks like "Bose Updater.aaNNN". These files have different name everytime when you update and are removed by BOSE updater after you finish updating.

4.Check the size of the firmware files, match them to the old firmware files, then rename the old firmware file to the matched one.

For example:
```
Bose Updater.fl7980 33KB
```
match with 
```
BayWolf_2.5.1_acorn_coeffs_signed.xuv  33KB
```
So rename "BayWolf_2.5.1_acorn_coeffs_signed.xuv" to "Bose Updater.fl7980". Follow such way and rename all these three firmware files.

5.Wait the device disconnection notification sound.

6.If there is a device disconnection notification sound,copy the "renamed" old firmware files to 
```
C:\Users\<username>\AppData\Local\Temp 
```
to replace the downloaded firmware files.Since there are only less than 2-5 seconds for replacing these "Bose Updater.aaNNN" firmware files. 
```
7/19/2019 23:14:50.806, Info, Device has disconnected
7/19/2019 23:14:57.870, Info, 1 BOSE CONNECTED DEVICE(S) WITH VID 0x05A7
```
Must do it as fast as you can, otherwise it may brick/damage the device.

7.Wait updater update the "cheated new firmware files"

8.When updating up to 100%, may show error message, just ignore it.

10.Check you device, the firmware is downgraded. 

  
  
The old firmware files:
```
https://github.com/avicoder/Boss-headphones-firmware
```



again, high risk!!!!!!!!!!!!!! i don't recommand you to do it, take you own risk!!!!!!!!! high risk.

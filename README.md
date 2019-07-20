
# How to downgrade bose QC35 ii firmware

I success downgrade QC35II firmware from 4.5.2 to 2.5.1.1182 then to 3.1.8.1835,and the device work well, for ANC, it's hard to say,better or not....

Who knows which is the best firmware? if someone knows, just file a issue and provide the firmware address. I may try it.

```
7/19/2019 23:19:24.701, Error, Expecting version to be 4.5.2.144, read 2.5.1.1182
7/19/2019 23:19:24.701, Info, Update: Waiting for external bootmode reset -> Error state
7/19/2019 23:19:29.763, Info, Internal version is 2.5.1.1182
7/19/2019 23:19:29.763, Info, External version is 2.5.1.1182
7/19/2019 23:19:29.763, Info, Device version is 2.5.1.1182
```

```
7/20/2019 09:22:55.212,  Error,      Expecting version to be 4.5.2.144, read 3.1.8.1835
7/20/2019 09:22:55.212,  Info,       Update: Waiting for external bootmode reset -> Error state
7/20/2019 09:23:11.885,  Info,       Internal version is 3.1.8.1835
7/20/2019 09:23:11.886,  Info,       External version is 3.1.8.1835
7/20/2019 09:23:11.886,  Info,       Device version is 3.1.8.1835
```

However, Don't recommand to downgrade it, high risk!!!!!!!!!!!!!! high risk, and high risk.

For windows:

When do updating, it will download the firmware to: `C:\Users\<username>\AppData\Local\Temp`
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
We can find, after finishing download firmware files from the internet, it will reboot the devices to reset it, so the device will disconnect to PC. And when the device disconnect, there is a notification sound from windows.

So, If we hear such notification sound, copy the old firmware files to `C:\Users\<username>\AppData\Local\Temp `to cheat updater, then it will push the old firmware files to device and update.


# Way of downgrade BOSE QC35 ii firmware

Environment: Bose Updater ver is 6.0.0.4388, win7, chrome 75.0.3770.142

1.Go to http://btu.bose.com/ , enter "a","d","v","up","down"

2.Click update button.

3.Check the name of the three firmware files in `C:\Users\<username>\AppData\Local\Temp `They are looks like "Bose Updater.aaNNN". These files have different name everytime when you update and are removed by BOSE updater after you finish updating.

4.Check the size of the firmware files, match them to the old firmware files.

5.Rename the old firmware file to the matched one.
 For example:
 ```
 Bose Updater.fl7980 33KB
 ```
   match with 
 ```
 BayWolf_2.5.1_acorn_coeffs_signed.xuv  33KB
 ```
   So rename "BayWolf_2.5.1_acorn_coeffs_signed.xuv" to "Bose Updater.fl7980". Follow such way and rename all these three firmware files.

6.Wait the first "device disconnection" notification sound.Since the devices reboot serveral times during updating, you can hear "device disconnection" notification sound several times. Remember, the first sound.....

7.If there is the first "device disconnection" notification sound,copy the "renamed" old firmware files to `C:\Users\<username>\AppData\Local\Temp `to replace the downloaded firmware files.There are only less than 5 seconds for replacing those "Bose Updater.aaNNN" firmware files. 
```
7/19/2019 23:14:50.806, Info, Device has disconnected
7/19/2019 23:14:57.870, Info, 1 BOSE CONNECTED DEVICE(S) WITH VID 0x05A7
```
  MUST MUST do it as fast as you can once hear the first notification sound of "device disconnection",otherwise it may brick/damage the device.You can re-update 4.5.2 several times to figure out when is the first "device disconnection" notification sound.

8.Wait updater update the "cheated new firmware files"

9.When updating up to 100%, may show error message, just ignore it.

 I encounter two different case:
 
    1).there wasn't progress bar on http://btu.bose.com/. but countdown.
    2).there was a progress bar, but went go 100%, error message shows out.
    
 However,at last downgrading are success. Just be patient and wait about 5 minutes.
 
 10.Check you device, the firmware is downgraded. 

  
  
The old firmware files:
```
https://github.com/avicoder/Boss-headphones-firmware
```


DISCLAIMER:

* High risk!!!!!!!!!!!!!! It may damage your device.
* I just share the way of downgrading QC35 ii firmware but don't recommand or encourage anyone to do it.
* Take you own risk!!!!!!!!! high risk.


# For BOSE

From the downgrade process, we know it's very very easy for BOSE to enable firmware downgrading.

Actually,for QC35 II,which firmware will be updated is controled by `http://downloads.bose.com/ced/baywolf/index.xml`
```
<INDEX REVISION="01.00.00">
  <DEVICE ID="0x4020" PRODUCTNAME="Bose QuietComfort 35 II">
    <HARDWARE REVISION="01.00.00">
      <RELEASE HTTPHOST="downloads.bose.com" LANGUAGES="en-us,es-mx,fr,de,zh-cn,ja,ko,it,pt-br,sv,nl,ru,pl" REVISION="4.5.2.144" URLPATH="/ced/baywolf/">
        <IMAGE CRC="0XFFFFFFFF" FILENAME="BayWolf_4.5.2_stack_plus_app.dfu" LENGTH="1942460" NOFORCE="1" REVISION="4.5.2.144" SUBID="0" />
        <IMAGE CRC="0XC64078AA" FILENAME="BayWolf_4.5.2_ext_signed.xuv" LENGTH="22618624" NOFORCE="0" REVISION="4.5.2.144" SUBID="1" TARGET="1" />
        <IMAGE CRC="0X8CF951D5" FILENAME="BayWolf_4.5.2_acorn_coeffs_signed.xuv" LENGTH="32944" NOFORCE="0" REVISION="4.5.2.144" SUBID="2" TARGET="3" />
      </RELEASE>
    </HARDWARE>
  </DEVICE>
</INDEX>
```

It include firmware downloading address,name,etc. BOSE can just modify or add more different firmwares in this XML, but they DO NOT DO anything.

BOSE lost customers' trust and breaken customers' hearts.Force their customer take high risk to do such "downgrade".

Some of the complains from `https://community.bose.com/t5/Around-On-Ear-Headphones/Bose-QC-35-ii-firmware-4-5-2/td-p/213820`

```
Either we're all going mad, and the tests by that site that measured the change in the ANC are a figment of our imagination。
```

```
Repeating over and over that "nothing was changed" is not helpful
```

```
BOSE: test the firmware use your own EARS!!!
```

```
no impact to ANC was detected ? This is just ridiculous!
```

```
It will still fail. I updated my old ones, fail. I updated my new replacements, fail. Its only fail fail fail...
```

```
Tried downgrading, tried resetting, nothing changed the situation.

Since I am in my 30 deays since purchase, I will return them and ask for my money back.

After reading all posts here I have no confidence Bose will do something about it in a reasonable amount of time.

I am so sorry to let them go, they were so comfortable.
```

```
i am sure about what i said my ears are good...
```


```
Yes, before the update we could not hear anything(almost). Now after the update we can hear more sound from outside.
```

```
I dont think all of us suddenly got a better hearing after using bose. We getting older every day..


Maaaybe that is what they want to say, use Bose and you will get a better hearing...AHAAAAA NOW I GET IT...

Truly disappointed with all of this
```

```
What Bose has done here is so unethical, I really don't have words for it.
```

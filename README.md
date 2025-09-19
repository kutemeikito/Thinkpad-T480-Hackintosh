# Lenovo ThinkPad T480 - OpenCore Configuation

![T480](https://raw.githubusercontent.com/kutemeikito/kutemeikito/refs/heads/master/assets/15.7.png)


# ⚠️⚠️⚠️ WARNING ⚠️⚠️⚠️
THIS BRANCH IS HIGHLY WIP, USABLE, BUT KEEP IT IN MIND THAT IT'S HEAVILY AMEND AND FORCE PUSH
AND I WON'T TAKE RESPONSIBLE IF THIS BRANCH BREAK SOMETHING, OR EVEN WIPE YOUR HARDDISK CLEAN

## ⚠️ Disclaimer
This guide is only for the Lenovo ThinkPad T480. I am NOT responsible for any harm you cause to your device. This guide is provided "as-is" and all steps taken are done at your own risk.

<details>
<summary><strong>💻 My Hardware</strong></summary>
<br>
These are the Hardware component I use. But this OpenCore configuation <strong>should still work</strong> with your device, even if the components are not equal.

Check the model of your WiFi & Bluetooth card. Intel cards should be compatible with itlwm (or AirportItlwm). If your card is from another manufacturer, please check if your card supports macOS. macOS Sonoma no longer supports Broadcom Wifi cards.

| Category  | Component                            |
| --------- | ------------------------------------ |
| CPU       | Intel Core i5-8350U                  |
| GPU       | Intel UHD Graphics 620               |
| SSD       | INTEL SSDPEKKF512G8L (512GB)         |
| Memory    | 24GB DDR4 2400Mhz                    |
| Camera    | 720p Camera                          |
| WiFi & BT | Intel Dual Band Wireless-AC 8265     |
| OS        | Windows 11 & MacOS Sequoia 15.5      |

*highly recommend to use adapter with extension cable

</details>  

</details>

&nbsp;

## Status

<details>  
<summary><strong>✅ What's working</strong></summary>
</br>
 
- [X] Intel WiFi & Bluetooth
- [X] Brightness / Volume Control
- [X] Battery Information
- [X] Audio (Audio Jack & Speaker)
- [X] USB Ports & Built-in Camera
- [X] Graphics Acceleration
- [X] Trackpoint / Touchpad
- [X] Power management / Sleep
- [X] FaceTime / iMessage (iServices)
- [X] HDMI
- [X] Automatic OS updates
- [X] Handoff / Universal Clipboard
- [X] Sidecar (Cable) / AirPlay to Mac
- [X] SIP / FireVault 2
- [X] USB-C
- [X] Dualbooting Windows / Linux (with OpenCore)

</details>

<details>  
<summary><strong>⚠️ What's not working</strong></summary>
</br>

- [ ] Safari DRM ```Use Chromium powered Browser or Firefox to watch Amazon Prime Video, Netflix, Disney+ and others```
- [ ] AirDrop & Continuity
- [ ] Fingerprint Reader (Disabled with NoTouchID kext)
- [ ] Thunderbolt 3
- [ ] Sidecar Wireless
- [ ] Apple Watch Unlock

</details>

<details>  
<summary><strong>🔄 Not tested</strong></summary>
</br>

- [ ] WWAN

</details>

<details>  
<summary><strong>🛜 Intel Wi-Fi Patch for macOS Sequoia </strong></summary>
</br>

**Intel Wi-Fi does not work on macOS Sequoia unless you install this patch.**

> Credit to [ResQre](https://github.com/ResQre) for these instructions

What you need
- Intel Wi-Fi Card (of course)
- Hackintool (for device path) + your favorite plist editor (in my case, OCAuxiliaryTools)
- [OpenCore Legacy Patcher](https://github.com/dortania/OpenCore-Legacy-Patcher) 

1. Open Hackintool and go to the Pcie menu, look for where it says "Intel Wireless" (in my case, Wireless 8260).
![ภาพถ่ายหน้าจอ 2024-12-26 เวลา 1 49 07 AM](https://github.com/user-attachments/assets/93566ae7-5b73-47ba-8d26-b1241e8c8dda)

2. Open a .plist editor (in this case, we'll use OCAuxiliaryTools), add the device path (without #), then add the following device details:

| Key   |      Data Type      |  Value |
|----------|:-------------:|:------:|
| IOName |  String | pci14e4,43a0|
| compatible |    String   | pci106b,117 |
| device-id | Data | A0430000 |
| device_type | String | Network Controller |
| model | String | BCM4360 802.11ac Wireless Network Adapter |
| name | String | pci14e4,43a0 |
| pci-aspm-default | Number | 0 |
| subsystem-id | Data | 17010000 |
| subsystem-vendor-id | Data | 6B100000 |
| vendor-xt | Data | E4140000 |

It should look like this:

![image](https://github.com/user-attachments/assets/2a7b1d5b-29a7-4740-aaba-9ce1eb661f3f)


Press save and reboot (no need for setting the kext up since it's already presented inside of the efi.)

3. If you done the setup correctly, you should be able to install the OCLP root patch.

![ภาพถ่ายหน้าจอ 2024-12-26 เวลา 2 36 01 AM](https://github.com/user-attachments/assets/6a44dd01-c7cf-4db5-8db7-e54683529687)

4. Install the patch, then you can remove the spoof id (or add the # instead) and Intel Wi-Fi should work without the need for Heliport.

![ภาพถ่ายหน้าจอ 2024-12-26 เวลา 2 41 25 AM](https://github.com/user-attachments/assets/8b7edcd6-3416-4b81-8f3f-192605804a65)


</details>

&nbsp;

## ⭐️ Feedback
Did you find any bugs or just have some questions? Feel free to provide your feedback using the Discussions tab.

&nbsp;

## Credits
> The ACPI patches and the style of this README are from [EETagent](https://github.com/EETagent/T480-OpenCore-Hackintosh).

> Thanks MultimediaLucario for his works on hackintosh EFI [Lenovo-ThinkPad-T480](https://github.com/MultimediaLucario/Lenovo-ThinkPad-T480).

> Thanks lolipuru for dual boot open-core issue [Thinkpad-T480-Opencore](https://github.com/lolipuru/Thinkpad-T480-Opencore).

## 📜 License

This repo is licensed under the [MIT License](https://github.com/valnoxy/t480-oc/blob/main/LICENSE).

OpenCore is licensed under the [BSD 3-Clause License](https://github.com/acidanthera/OpenCorePkg/blob/master/LICENSE.txt).

<hr>
<h6 align="center">© 2018 - 2024 valnoxy. All Rights Reserved. 
<br>
By Jonas Günner &lt;jonas@exploitox.de&gt;</h6>
<p align="center">
	<a href="https://github.com/valnoxy/t480-oc/blob/main/LICENSE"><img src="https://img.shields.io/static/v1.svg?style=for-the-badge&label=License&message=MIT&logoColor=d9e0ee&colorA=363a4f&colorB=b7bdf8"/></a>
</p>

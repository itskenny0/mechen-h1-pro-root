# mechen-h1-pro-root
Reverse engineering / rooting information regarding the mechen h1 pro Android MP3 player
Not to be confused with the non-pro Mechen H1, which seems to be more locked down judging by information on the internet.

The H1 Pro seems to have slipped in price massively and can be had for around 30$ on sale on aliexpress, making it an interesting target.

The rooted kernel in this repo is specifically for T04_50_2_16_4inch_M404_ST7701S_sh1282G003_MECHEN_V1.0_20250305. This is an Android 9 build.
The chip in the device is MT6750V/C, 2G RAM, 16G flash. USB port does not seem to support OTG. SD cards up to 1 TB tested readable in the SD card slot.
The screen is 800x480, which is okay as the device is very small. There is some bloatware on it, which I recommend removing. I would also suggest reinstalling your own music streaming apps instead of using the preinstalled ones. I recommend Package Manager for debloating the system: https://f-droid.org/packages/com.smartpack.packagemanager/

# Steps to get rooted kernel image
The repo contains a rooted kernel for the aforementioned firmware version, but if yours differs, follow these steps to get your own image.
* Use mtkclient to connect to the device pre-boot: https://github.com/bkerler/mtkclient/
* Using mtkclient, take a backup of your entire device: https://github.com/bkerler/mtkclient/
* mtkclient will generate a file named boot.bin, rename this to boot.img and copy to a SDcard, insert into device.
* Install Magisk app and patch the boot.img.

# Unlock the bootloader
!!! Following these steps will erase the internal storage, backup your stuff !!!
* Go into Settings > System > About Device
* Repeatedly tap on the model name (MECHEN H1-Pro) until you are a developer
* In developer menu one level up, enable OEM unlocking and adb debugging
* Check if device is present: adb devices
* A popup on your device will ask you to trust the computer, do that.
* Reboot the device to bootloader via adb: adb reboot bootloader
* Unlock the bootloader: fastboot flashing unlock
* On the device, confirm unlocking. This will erase userdata.

# Flash rooted kernel image
* Open mtkclient, reboot the device with USB connected and flash the boot.img you generated, or, if you are on the same firmware as stated above, you can use the image in the repo, to the boot partition.
* After the player has booted, open the Magisk app and install again. It should now offer you to patch the kernel on-device. Do this and reboot again.
* You are rooted.

# To be done
* GSI testing

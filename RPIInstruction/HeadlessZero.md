# Set up a headless Pi Zero

## What you need

- Raspberry Pi Zero
- microSD card
- Power
- Computer

## Downloads

You need Raspbian, as well as Etcher for the following steps

- [Raspbian Stretch Lite](https://www.raspberrypi.org/downloads/raspbian/) -  Get the zip file.
- [Etcher](https://etcher.io) - to burn Raspbian on your microSD card

After downloading Raspbian, unzip it to get the `.img` file.

## Burn Raspbian on microSD Card

1. Launch Etcher (Install it first if not already).
2. Select your `.img` file under `Select image`.
3. Select your microSD card under `Select drive`.
4. Press `Flash!`.
5. When the process is finished, reinsert your microSD card for the next step.

## Configure SSH and Wi-Fi

1. Move to your microSD card folder. `cd /Volumes/boot/` or the equivalent.
2. Activate SSH. `touch ssh`
3. Create Wi-Fi file. `sudo nano wpa_supplicant.conf`
4. Paste the following into the file. Replace COUNTRY_CODE, YOUR_WI-FI_SSID and YOUR_PASSWORD with the required information.

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=COUNTRY_CODE

network={
    ssid="YOUR_WI-FI_SSID"
    psk="YOUR_PASSWORD"
    key_mgmt=WPA-PSK
}
```

4. Save the file.
5. Eject the microSD card.

## Boot your Pi

Now we need to get your Pi up and running.For that, insert the microSD card into your pi and connect it to power.

## Connect to your Pi

When your Pi has booted, we can finally connect to it via SSH.

1. Launch Terminal.
2. SSH into your Pi. `ssh pi@raspberrypi.local`
3. Enter password. `raspberry`

Now we should be connected. First things first, change the password.

1. Enter `passwd` into Terminal.
2. Create a new password and store it somewhere save.

Also, we should change the  Hostname. This is usefull for when you have multiple Pis on your network.

1. Go into the Pis configurations. `raspbi-config`.
2. Go to network.
3. Set a new Hostname, e.g. homepi.
4. Finish and reboot Pi

You now need to connect again to your Pi via SSh, but this time use your new  Hostname instead of raspberrypi, e.g. `ssh pi@homepi.local`

## Update Pi

Finally we need to update everything on your Pi.

1. `sudo apt-get update`
2. `sudo apt-get upgrade`
3. Reboot Pi

## Finish

Congratulation, you have just successfully set up a headless Pi Zero. Now you can install things like Homebridge or Plex on it. Happy hacking :)

## Disclosure

This [article](https://infinitediaries.net/using-a-raspberry-pi-zero-w-to-add-a-camera-and-a-xiaomi-air-purifier-2-to-homekit-via-homebridge/) helped me while creating this summary.

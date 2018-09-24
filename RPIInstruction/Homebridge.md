# Install Homebridge on Raspberry Pi

## Prerequisit

Before you can start with installing Homebridge on your Raspberry Pi, you need to have one with Raspbian already up and running. If this is not the case, see [here](https://www.losant.com/blog/getting-started-with-the-raspberry-pi-zero-w-without-a-monitor) for more information on how to install Raspbian and how to get your Pi to work.

## Setup

### Install Node.js

To get [Homebridge](https://github.com/nfarina/homebridge) up and running, you first need to install Node.js on the Pi. For that, run the following command to download ``nodejs``.

```bash
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - 
```

Then install ``nodejs``.

```bash 
sudo apt-get install -y nodejs 
```

This may take a while.

**Note: If you try to install Homebridge on a Pi without an ARMv7 chip (eg. Pi Zero, Pi 2, Pi 1) see [down below](#install-node.js-on-older-pis-(armv6-chip)) on how to install Node.js.**

### Install Homebridge

Next you need to install Homebridge itself.

```bash
sudo npm install -g --unsafe-perm homebridge 
```

Congrats 🎉, Homebridge is now successfully installed. But to use it and to add it to the Home app, you need to install some install some plugins.

## Add Homebridge to Home

After you have installed some plugins, you can add homebridge to the home app. For that start homebridge and then go to the Home app.

Tap ``Add Accessory``, go to `I don't have a QR-Code` and input your setup code manually. It probably is `031-45-154`. Now you can add Homebridge to the Home app, as well as your accessories (plugins).

## Install Node.js on older Pi's (armv6 chip)

Run these commands to download and install the correct ``nodejs`` library. This will take a while to finish.

```bash
wget https://nodejs.org/dist/v6.9.5/node-v6.9.5-linux-armv6l.tar.xz
tar xJvf node-v6.9.5-linux-armv6l.tar.xz
sudo mkdir -p /opt/node
sudo mv node-v6.9.5-linux-armv6l/* /opt/node/
sudo update-alternatives --install "/usr/bin/node" "node" "/opt/node/bin/node" 1
sudo update-alternatives --install "/usr/bin/npm" "npm" "/opt/node/bin/npm" 1
```

## Troubleshooting

### Home can't find/add Homebridge

If you have this problem, you probably need to [disable IPv6 support](https://github.com/nfarina/homebridge/issues/607). For that, open ``cmdline.txt``.

```bash
sudo nano /boot/cmdline.txt 
```

And add the following command.

```bash
ipv6.disable=1 
```

All you have to do now is save, exit, reboot your Pi, and restart Homebridge.

```
sudo reboot
homebridge
```

Now Home should be able to find Homebridge and add it.

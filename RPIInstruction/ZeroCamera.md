# Install 

## Summary

Transform your Raspberry Pi into a home security camera with homebridge and [homebridge-camera-rpi](https://github.com/moritzmhmk/homebridge-camera-rpi). 

## Prerequisite

You need a Raspberry Pi running Homebridge for this to work

## Install 

**Activate the camera module.**

Type `raspi-config`, go to `Interfaces` and turn of the camera module.

**Load camera module**

Type `sudo nano /etc/modules` and add the following to the end of the file

```
# Camera with v4l2 driver
bcm2835-v4l2
```

**Install ffmpeg**

`sudo apt get install ffmpeg`

**Install homebridge-camera-rpi**

`sudo npm install -g homebridge-camera-rpi`

This will install the required plugin for the camera to be shown in Homebridge.

**Edit `config.json`**

Add the camera to Homebridge.

`sudo nano ~/.homebridge/config.json`

Add the following to the file.

```
{
    "platforms": [
        {
            "platform": "rpi-camera",
            "cameras": [{"name": "Pi Camera"}]
        }
    ]
}
```

**Restart Homebridge**

`sudo systemctl restart homebridge`

## Issues

Give permission to user for camera at start up.

`sudo usermod -a -G video homebridge`

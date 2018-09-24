# Install Pi Temperature Plugin

## Prerequisit

Before installing the [Pi Temperature](https://github.com/markwj/homebridge-pi) plugin, you need a Raspberry Pi up and running, as well as Homebridge installed and running.

## Install Pi Temperature Plugin

```bash
sudo npm install -g homebridge-pi 
```

With homebridge-pi successfully installed, it is time to add it as an accessory to Homebridge. First go into the homebridge direcotry.

```bash
cd ~/.homebridge 
```

Next you want to create a file called ``config.json`` if it does not exist already.

```bash
sudo touch config.json 
```

Finally you want to open the file and add the accessory.

```bash 
sudo nano config.json 
```

Copy and paste the following json code to add the accessory.

```json
{
    "bridge": {
        "name": "Homebridge",
        "username": "CC:22:3D:E3:CE:30",
        "port": 51826,
        "pin": "031-45-154"
    },

    "description": "This is the configuration file to your Homebridge server.",

    "accessories": [
        {
            "accessory": "PiTemperature",
            "name": "Raspberry Pi Temperature"
        }
    ],

    "platforms": [
    ]
}
```

Now save the file and hit enter to exit the file.

Finally restart homebridge and you can add your Pis temperature to the home app.

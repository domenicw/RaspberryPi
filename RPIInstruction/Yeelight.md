# Install Yeelight Plugin

## Prerequisit

Before installing the [homebriddge-yeelight](https://www.npmjs.com/package/homebridge-yeelight) plugin, you need a Raspberry Pi up and running, as well as Homebridge installed and running.

## Turn on Developer Mode

Enter developer mode of your Yeelight Bulb via the Yeelight app.

## Install Yeelight Plugin

```bash
sudo npm install -g homebridge-yeelight 
```

With homebridge-yeelight successfully installed, it is time to add it as an accessory to Homebridge. First go into the homebridge direcotry.

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
    "platforms": [
        {
            "platform" : "yeelight",
            "name" : "yeelight"
        }
    ]
}
```

Now save the file and hit enter to exit the file.

Finally restart homebridge and you can add your Yeelight to the home app.


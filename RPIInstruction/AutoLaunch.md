# Automatically Start Homebridge at Reboot

## Prerequisit

You need a Raspberry Pi up and running, as well Homebridge installed.

## Installation

### Create Startup Files

#### Create the first file.

```bash
sudo nano /etc/default
```

Copy the following code into it.

```bash
# Defaults / Configuration options for homebridge
# The following settings tells homebridge where to find the config.json file and where to persist the data (i.e. pairing and others)
HOMEBRIDGE_OPTS=-U /var/lib/homebridge

# If you uncomment the following line, homebridge will log more 
# You can display this via systemd's journalctl: journalctl -f -u homebridge
# DEBUG=*
```

#### Create the second file

```bash
sudo nano /etc/systemd/system
```

Copy the following code into it.

```bash
[Unit]
Description=Node.js HomeKit Server 
After=syslog.target network-online.target

[Service]
Type=simple
User=homebridge
EnvironmentFile=/etc/default/homebridge
# Adapt this to your specific setup (could be /usr/bin/homebridge)
# See comments below for more information
ExecStart=/usr/bin/homebridge $HOMEBRIDGE_OPTS
Restart=on-failure
RestartSec=10
KillMode=process

[Install]
WantedBy=multi-user.target
```

### Configuration

1. Add new system user.

```bash
sudo useradd -M --system homebridge
```

Grant user access to newly created homebridge file.

```bash
sudo chmod -R 0777 /var/lib/homebridge
```

And finally copy all your homebridge file to the directory.

```bash
sudo cp -r ~/.homebridge/* /var/lib/homebridge
```

From now on you need to add new accessories to the config file at `/var/lib/homebridge`.

### Enable Service

```bash
sudo systemctl daemon-reload
sudo systemctl enable homebridge
sudo systemctl start homebridge
```

You can check the status of the serice at all time by calling 

```bash
sudo systemctl status homebridge
```

## Disclosure

This was written with the help of this Github [gist](https://gist.github.com/johannrichard/0ad0de1feb6adb9eb61a/).

# pi-top-install
Do you want to run the standard raspbian jessie on the pi-top?
In this repository you find tips, tricks and scripts to install the necessary capabilities to control
the pi-top hardware using a standard raspbian jessie distribution.

**1 - Battery status display widget (released)**

See separate repository https://github.com/rricharz/pi-top-battery-status

This program has been tested on raspbian jessie and should work well with any distribution. Do not forget to turn **i2c** on in *Raspberry Pi Configuration*. The program also needs i2c-tools installed (install with the command "sudo apt-get install i2c-tools". The program will display the battery status, and will shut down the Raspberry Pi if the battery capacity is low and not charging. But on a standard raspbian system it will not be able to turn off the pi-top hub and the power to the Raspberry Pi. It will therefore not protect the battery from further depleting. The pi-top-hub still needs to be turned off manually with the switch.

**2 - Python program to set the screen brightness (tested)**

Usage (new_value is a screen brightness value between 3 and 10):
```
brightness new_value
brightness increase
brightness decrease
```

**3 - Python program and system service to turn hub-power off after shutdown (under test)**

This program will help to protect your battery by shutting of the pi-top-hub-controller
after a shutdown of the Raspbery Pi

**Installation instructions for 2 and/or 3*

To download this repository, open a terminal and type:
```
cd Downloads
git clone git://github.com/rricharz/pi-top-install
cd pi-top-install
chmod +x install*
```

Make sure that **spi** is turned on in *Menu/Preferences/Raspberry Pi Configuration/Interfaces*.

Make sure that yor system is up-to-date:
```
sudo apt-get update
sudo apt-get upgrade
```

If you want to install 3 (automatic poweroff), you also need to make sure that your system
is updated to the newest, so called systemd, bootup and shutdown process:
```
sudo apt-get dist-upgrade
```

Now you can install phyton-dev and py-spidev. Both are needed to access the hub-controller
```
./install-spidev
```

To install 2 (brightness):
```
./install-brightness

To install 3 (automatic poweroff)
```
./install-poweroff
```

You are encouraged to contribute to this repository. See https://guides.github.com/activities/hello-world/
to learn how to create, modify and submit a branch. Or open an issue in this repository to report problems or suggestions.

The contributions in this repository are distributed in the hope that they will be useful, but WITHOUT ANY WARRANTY;
without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. The owner of this repository
is not affiliated with pi-top.

For problems and suggestions, please open an issue in this repository.

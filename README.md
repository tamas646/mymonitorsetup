# mymonitorsetup
Multi-monitor setup manager with custom profiles.

It supports changing the Gnome **dashtopanel** extension's settings with dconf-cli.

## Usage
Just assign a keyboard shortcut to the command `mymonitorsetup` and then you will be able to switch easily between monitor setups defined in `/etc/mymonitorsetup/profiles.ini`.

## Config example (for two monitors)

```ini
[DEFAULT]

window-width = 400    # profile switcher window's width in pixels
window-height = 690   # profile switcher window's height in pixels

[exampleprofilename]
	# these are dashtopanel's settings
	dashtopanel-multi-monitors = true
	dashtopanel-primary-monitor = 1
	dashtopanel-show-showdesktop-hover = true
	dashtopanel-stockgs-keep-top-panel = false
	dashtopanel-stockgs-keep-dash = false
	dashtopanel-group-apps-label-max-width = 80

	output[0] = eDP-1      # the first monitor's device-name
	mode[0] = 1920x1080    # the first monitor's resolution
	pos[0] = 1280x400      # the first monitor's position
	primary[0] =           # set as default monitor

	output[1] = DP-1       # same but for the second monitor
	mode[1] = 1280x1024    # same but for the second monitor
	pos[1] = 0x0           # same but for the second monitor
```

You can find a full list of available settings for dashtopanel by executing `dconf list /org/gnome/shell/extensions/dash-to-panel/`.

This script using **xrandr** to apply the changes, therefore every monitor settings given in the config are exactly the same as the xrandr options.
For these options see `man xrandr`.

## Installation
- You can either [download](https://github.com/tamas646/mymonitorsetup/raw/main/mymonitorsetup_1.2.0_all.deb) and install the deb package or use the source code and setup it yourself.

- If you wish, you can install it from my apt repository too:

  ```sh
  sudo echo "deb http://apt.ptamas.hu/main/ ./" > /etc/apt/sources.list.d/apt.ptamas.list
  wget -O- https://apt.ptamas.hu/ptamas-pub.gpg |sudo apt-key add -
  apt update && apt install mymonitorsetup
  ```

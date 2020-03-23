# check_rpi_temperature

Raspberry Pi temperature plugin for Nagios/Icinga

Threshold for warnings is 50°C, for critical it is 60°C.
A different warning threshold can be set, the threshold for critical level is calculated from this by adding 10°.

## Installation

I usually install additional plugins under `/usr/local/lib/nagios/plugins`.
So, it works out of the box, if you just do:

```
mkdir -p /usr/local/lib/nagios/plugins
cd /usr/local/lib/nagios/plugins
wget https://raw.githubusercontent.com/check-plugins/check_rpi_temperature/master/check_rpi_temperature
chmod +x check_rpi_temperature
```

The script uses `utils.sh` from `monitoring-plugins-common` is required. It can be installed on Debian by running:

```
apt-get install monitoring-plugins-common
```

The script depends on `vcgencmd` from `libraspberrypi-bin`.

## Example

```
root@monitor:~# /usr/local/lib/nagios/plugins/check_rpi_temperature
OK; 41.2'C
root@monitor:~# 
```

You may modify the warning threshold by just passing the maximum temperature:

```
root@monitor:~# /usr/local/lib/nagios/plugins/check_rpi_temperature 40
WARNING; 40.1'C
root@monitor:~# /usr/local/lib/nagios/plugins/check_rpi_temperature 30
CRITICAL; 40.1'C
root@monitor:~# 
```

The value for the critical temperature is always warning + 10°.

## Support

I have not the time (yet) to provide professional support for this project. But feel free to submit issues and PRs, I'll check for it and honor your contributions.

## License

The whole project is licensed under GPL license. Stay fair.

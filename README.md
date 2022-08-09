# Munin Plugin for Comet Server

This is a set of scripts for [Munin](https://munin-monitoring.org/) to export metrics from a running Comet Server instance over the Comet Server API.

## Requirements

- Python 3.8.10 or later
- Munin 2.0.69 or later

[Recommended Munin Ubuntu install instructions](https://www.hackerxone.com/2021/10/14/steps-to-install-munin-monitoring-tool-on-ubuntu-20-04-lts/)

## Installation instructions

The following instructions will cover installing the comet-munin plugin on Ubuntu 20.04.

A lot of the instructions here need to be run as root, so run `sudo -i`  

Download , extract, and move the scripts to `/usr/share/munin/plugins`.  
Example:  
`cd ~/Downloads`  
`unzip comet-munin-plugin-main.zip`  
`cd ~/Downloads/comet-munin-plugin-main`  
`mv comet_* /usr/share/munin/plugins`

Set all the files aside from `comet_server.py` as executable and Create a symbolic link of these files to `/etc/munin/plugins`.  
```
for plugin in comet_jobs_classification comet_jobs_status comet_latency comet_online_devices comet_server_history comet_uptime; do
  chmod +x "/usr/share/munin/plugins/$plugin"
  ln -s "/usr/share/munin/plugins/$plugin" "/etc/munin/plugins/$plugin"
done
```

Once done, restart Munin and Munin node `systemctl restart munin munin-node`

## Generated metrics

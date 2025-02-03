---
layout: default
title: Client
nav_order: 10
---

{: .no_toc }

Just the Docs has some specific configuration parameters that can be defined in your Jekyll site's \_config.yml file.
{: .fs-6 .fw-300 }

# Table of contents
1. TOC
{:toc}

# Download

You can find the client downloads on github, [here](https://github.com/ao-data/albiondata-client/releases).

Download stats can be found [here](https://tooomm.github.io/github-release-stats/?username=ao-data&repository=albiondata-client).

<!-- # Installing

## Windows

## MacOS

## Linux -->

# Command Line Options
You can see all of the current available command line parameters by launching the executable with
`"C:\Program Files\Albion Data Client\albiondata-client.exe" -h` or by adding `-h` to the shortcut.

At the time of writing the following are the available configuration options:
```
"C:\Program Files\Albion Data Client\albiondata-client.exe" -h
  -d	If specified no attempts will be made to upload data to remote server.
  -debug
    	Enable debug logging.
  -events string
    	Whitelist of event IDs to output messages when debugging. Comma separated.
  -events-ignore string
    	Blacklist of event IDs to hide messages when debugging. Comma separated.
  -i string
    	Base URL to send PUBLIC data to, can be 'nats://', 'http://' or 'noop' and can have multiple uploaders. Comma separated. (default is "http+pow://pow.west.albion-online-data.com" or "http+pow://pow.east.albion-online-data.com" determined by the game server you connect to)
  -ignore-decode-errors
    	Ignore the decoding errors when debugging
  -l string
    	Listen on this comma separated devices instead of all available
  -minimize
    	Automatically minimize the window.
  -no-limit
    	Use all available CPU cores
  -o string
    	Parses a local file instead of checking albion ports.
  -operations string
    	Whitelist of operation IDs to output messages when debugging. Comma separated.
  -operations-ignore string
    	Blacklist of operation IDs to hide messages when debugging. Comma separated.
  -output-file
    	Enable logging to file.
  -p string
    	Base URL to send PRIVATE data to, can be 'nats://', 'http://' or 'noop' and can have multiple uploaders. Comma separated.
  -record string
    	Enable recording commands to a file for debugging later.
```

## Disable Start With Windows
1. Open up the program `Task Scheduler`.
1. Click on the `Task Scheduler Library` in the left side pane.
1. Find the task with the name `Albion Data Client`.
1. Right-click `Disable` to disable the task.

# Troubleshooting

Starting the client via the command line will allow the error message to persist.
- Windows
  - Open a run command prompt window with `WIN + r`
  - Enter `"C:\Program Files\Albion Data Client\albiondata-client.exe"`
  - View application output
- MacOS
  - Open a terminal `COMMAND + SPACE` and type `terminal`
  - Enter `/path/to/albiondata-client`
  - View application output
- Linux
  - Open a terminal (too many ways to list, if you use Linux, you should know how)
  - Enter `/path/to/albiondata-client`
  - View application output

## Client crashing
### Device/Adapter Errors

Includes the following Error Messages:
- "No such device exists"
- "Error opening adapter: The system cannot find the device specified. (20)"
- "eth0: You don't have permission to capture on that device (socket: Operation not permitted)" (Linux/MacOS specific)

This means the client can't attach it self to the network interface to capture Albion Online data.

- Windows
  - Open a command prompt
  - Type `ipconfig.exe /all`
  - Look for the network adapter that give's you connectivity and find the `Physical Address` line:![Alt text](../images/ipconfig.png)
  - Start the client with the `-l` (lower case L) argument, replacing the physical address of your card: `"C:\Program Files\Albion Data Client\albiondata-client.exe" -l "B4-2E-99-31-90-E2"`
- MacOS
  - Open a terminal
  - Type `ifconfig`
  - Look for the network adapter that give's you connectivity and find the `Physical Address` line:![Alt text](../images/macos-ifconfig.png)
  - Start the client with the `-l` (lower case L) argument, replacing the physical address of your card: `/path/to/albiondata-client -l "14:7D:DA:DB:C6:29"`
- Linux (essentially the same as MacOS)
  - Open a terminal
  - Type `ifconfig`
  - Look for the network adapter that give's you connectivity and find the `Physical Address` line:![Alt text](../images/linux-ifconfig.png)
  - Start the client with the `-l` (lower case L) argument, replacing the physical address of your card: `/path/to/albiondata-client -l "7E-13-57-B4-C4-3B"`

### MacOS/Linux needs sudo

[Original developer discussing the issue.](https://github.com/regner/albiondata-client/issues/125)

Running the Albion Online Data client with sudo is the easiest way to get going. But, you can work around needing full sudo if you understand Linux/MacOS permssions.

The following has been copied and modified to fit this project's use.

Note: `aod` group is short for "Albion Online Data". You'll need to substitute `/path/to/albiondata-client` with the actual path to your client.

```
Add a capture group and add yourself to it:

Source: https://github.com/bettercap/bettercap/issues/783#issuecomment-1021912001
sudo groupadd aod
sudo usermod -a -G aod $USER

Next, change the group of tcpdump and set permissions:

sudo chgrp aod /path/to/albiondata-client
sudo chmod 750 /path/to/albiondata-client
```

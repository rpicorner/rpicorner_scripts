# How to setup the Raspberry Pi as a torrent box

A Raspberry Pi Torrentbox is a great way to have a cheap affordable always-on torrent machine. If you’re a heavy or light torrent user, then this still works pretty well for both.

Using the Pi as a Torrentbox is an excellent way to save on power, especially if you want to run it 24/7. It also helps separate your downloads from your main PC and help protect you against malicious files.

### Transmission

In this guide we will setup Transmission. Transmission is an excellent solution for torrenting on the Raspberry Pi. It is a relatively light client that is designed to use few resources,
and have a light web interface that alows to interact with it using a web browser.

# Equipment

Below is the equipment you need to follow this tutorial:

## Recommended

- [Raspberry PI](https://bit.ly/36T6lqL)
- [Micro SD Card](https://amzn.to/2JBK4Fd) 4GB is the bare minimum, but the bigger the card more files can be shared.

## Optional
The first thing that we must do before we
- [External Hard Drive](https://amzn.to/37JL1mS) For reliable data storage (SDCards tend to fail after a while due to enourmous amount of operations the OS need to do)
- [Raspberry PI Case w/ Fan](https://amzn.to/2VSi16N) For cooling the board to prevent over temperatures and performance throttle

Note: The USB ports on the Raspberry Pi might not be enough to power an external drive so you might need to invest in a [powered USB hub](https://amzn.to/3ovA27h).

# Before start

To follow this tutorial you just need to have access to a terminal on the Raspberry Pi, it can be directly plug a keyboard, mouse and monitor or just access it remotly via SSH.
This tutorial was developed and tested on the Raspberry PI OS, but any linux distribution that runs on the Raspberry Pi should work.

# Setting up Transmission

The first thing that we must do before we proceed is to make sure everything is up to date.

```
sudo apt update && sudo apt upgrade -y
```

Now that we have our operating system up to date, we can now proceed to installing the Transmission software to our Raspberry Pi. Since Transmission is very popular it is already present on most distributions software repositories.
On the Raspberry Pi OS is as simple as running the following command:

```
sudo apt install transmission-daemon
```

Then, we must create the directories to hold the files. Note: check the hard disk tutorial to store the files on an external HDD.

```
mkdir -p ~/torrents/complete
mkdir -p ~/torrents/incompleted
```

Now we need to edit the transmission configuration file to use the created directories. The configuration file is in the path /etc/transmission-daemon/settings.json.
You can use nano to edit the file

```
sudo nano /etc/transmission-daemon/settings.json
```

I recommend change the folowing parameters, but you can change anything that you want. The list with the meaning of each fiels can be found in [this link](https://github.com/transmission/transmission/wiki/Editing-Configuration-Files).

```
"download-dir" : ~/torrents/complete,
"incomplete-dir" : ~/torrents/incompleted,
"incomplete-dir-enabled" : true,
```

After saved the changes the service must be restarted to use the new configurations.

```
sudo service transmission-daemon restart
```

Now everything should be up and running. To access the torrent page go to your browser and type:

```
http://<rpi_ip>:9091
```








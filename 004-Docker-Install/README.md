# How to install docker on the Raspberry Pi

Docker is a tool for creating, deploying, and running applications in containers. The software is popular among developers as it speeds up the development process and does not use a lot of resources. It is also very useful to run various servers in the same machine without the applications interfering with each other.

Docker containers are lightweight, especially compared to virtual machines. This feature is especially valuable if you are a Raspberry Pi user.

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

# Setting up Docker

The first thing that we must do before we proceed is to make sure everything is up to date.

```
sudo apt update && sudo apt upgrade -y
```

Now we need curl in our system to download the docker installation script.

```
sudo apt install curl
```

Move on to downloading the installation script with:

```
curl -fsSL https://get.docker.com -o get-docker.sh
```

Execute the script using the command:

```
sudo sh get-docker.sh
```

This installs the required packages for your Raspbian Linux distribution.

# Configuration

By default, only users who have administrative privileges (root users) can run containers. If you are not logged in as the root, one option is to use the sudo prefix.
However, you could also add your non-root user to the Docker group which will allow it to execute docker commands.

The syntax for adding users to the Docker group is:

```
sudo usermod -aG docker [user_name]
```

# Test

To test your docker installation you can run the command:

```
docker run hello-world
```

If it runs successefully your docker installation is working properly.



---
layout: post
title: Initial Jetson Setup
subtitle: First steps to set up a Jetson TX2 for LeConte
author: "Ben Klein"
---

So you've got a Jetson TX2 and you're not quite ready to go?

Here's a tutorial on getting your new TX2 set up and ready to go in a LeConte cluster!

## Foreword

Throughout this tutorial I expect that you have experience with SSH, Networking, VirtualBox (or other hypervisor), and Bash (or another shell).

I skim over some parts to make it easier to use as a reference document. I won't cover things like how to configure your network, or how to install a VirtualBox VM, you can find that that information is abundant online.

# First Boot

These instructions differ from the provided 'quick start' instructions that Nvidia provides, you won't need a mouse or keyboard here since the Jetson should have already come pre-flashed. We'll be doing setup over a LAN, although you could also do so with a direct ethernet connection from your computer to the board.

When you plug in the Jetson to power for the first time, you should see a single power LED come on.

Now you can turn on the Jetson using one of the four buttons on the edge of the board, press the one closer to the center, labeled "POWERBTN" in small print.

Once your Jetson has powered on, you should ensure your ethernet is plugged in, and that you know the IP address of your Jetson.

# Step 1:
## Install Nvidia drivers

`ssh nvidia@<jetsons-ip.address>`
With password 'nvidia'

You'll probably get a big flashy message:

```text
****************************************************************

Welcome,

Instructions on how to install the NVIDIA Linux driver binary
release which is located at : ${HOME}/NVIDIA-INSTALLER

Step 1)
Change directories into the NVIDIA installation directory:
    cd ${HOME}/NVIDIA-INSTALLER

Step 2)
Run the installer script to extract and install the NVIDIA
Linux driver binary release:
    sudo ./installer.sh

Step 3)
Reboot the system to have the Ubuntu Desktop UI come up.

NOTE:
username: nvidia
password: nvidia

Visit https://developer.nvidia.com/embedded-computing to
download the latest software release and product documentation


****************************************************************
```

You'll want to follow those instructions,

```bash
cd ~/NVIDIA-INSTALLER
sudo ./installer.sh
sudo reboot # assuming it worked
```

# Step 2:
## System hostname

Since this Jetson will be used in a network, we need to make sure we change the hostname before plugging it in with other Jetsons, since two jetsons with the same hostname will conflict.

```bash
sudo vim/nano /etc/hostname # change to something you'll remember
sudo hostname <new_hostname>
sudo vim /etc/hosts # change the old hostname to the new one
sudo reboot
```

Now you can hook this up to a router or switch with the rest of your Jetson cluster. You'll need a DHCP host somewhere if you're not using a router.

# Step 3:
## Install the Jetpack L4T kit on an Ubuntu 16.04 host

You can go to https://developer.nvidia.com/embedded-computing to find the download for the "Jetpack L4T 3.0" or newer. You should get a .run file.

You will need an Ubuntu 16.04 host computer, or virtual machine to use the `.run` file in, we used a VirtualBox VM.

Once you've got the file downloaded (and inside the 16.04 VM), you should run it to install all the host libraries.

# Step 4:
## Install the Jetpack kit onto the Jetson

During the Jetpack setup, you should see two sections of install items, the first was for the host, and the second section is for Jetson TX2 applications, libraries, etc.

Now you should select to install everything *except* "Flash Target OS" since we already have a working image on the Jetson.

Once you click next, it should download the requirements and prompt you for the Jetson's IP and user/password combo. Use nvidia/nvidia for authentication here.

Once started, it will take awhile, so while I'm waiting for this setup to finish I'm writing this post. Note: it might take a really long time.

Alright, it's done, at the end of the terminal window output it should tell you to close it or just press enter.

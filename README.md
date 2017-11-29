CCM for x86
# EZ-Crypto Coin Miner (Based on Ubuntu MATE 16.04.03 Xenial Xerus)

This is a work in progress that is meant to document the procvess to create a simple way to turn any machine into a Crypto Coin Miner. At this point, this is based on using [Ubuntu-MATE](https://ubuntu-mate.org/); not because Ubuntu MATE is superior but because it was what I was most familiar using.

As you might imagine, this is not a formal effort and if you choose to use what I have made available here on this site, everything you do is "at your own risk". You have been warned.

If you find an issue, I would appriciate you letting me know via email monteymonero@gmail.com

***

# Table of Contents
- [Software](#software)
    - [CUBIC](#info-cubic)
        - [Install CUBIC](#Install Cubic)

***

[(Back to top)](#table-of-contents)


# Software

### CUBIC
Cubic is an acronym for a GUI application to create a customized bootable Ubuntu Live CD (ISO) image. **C**ustom **Ub**untu **I**SO **C**reator.


 ### Things to install:
        htop
        nmon
        screen
        mc
        tree
        openssh
            Port 22022


### Things to adjust:
        vm.swapiness=10
        vm.nr_hugepages=512
        vm.vfs_cache_pressure=50
        create user 
            adduser ccminer
            usermod -aG sudo ccminer
            Edit /etc/sudoers with visudo
            
         Enable Auto-login
         Create File: nano /etc/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
         Insert Following into file:
         [SeatDefaults]
         greeter-session=lightdm-gtk-greeter
         autologin-user=ccminer 
         autologin-user-timeout=0

            
            

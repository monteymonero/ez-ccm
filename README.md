CCM for x86
# EZ-Crypto Miner (Ubuntu Server 16.04.03 "Xenial Xerus")

This is a WIP that is meant to document the process to create a simple way to boot a computer via PXE/USB and have it participate in Crypto Mining. At this point, this is based on using [Ubuntu Server](https://ubuntu.org/); not because Ubuntu is superior but because it was what I was most familiar using.

This is not a formal/production ready effort and if you choose to use what I have made available here on this site, everything you do is "at your own risk". You have been warned.

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
        tmux
        minicom
        openssh
        glances
    # gcc 7.1
    sudo add-apt-repository ppa:jonathonf/gcc-7.1
    sudo apt-get update
    sudo apt-get install gcc-7 g++-7
### Things to adjust:
        vm.swapiness=10
        vm.nr_hugepages=512
        vm.vfs_cache_pressure=50
        create user 
            adduser <username>
            usermod -aG sudo username
            Edit /etc/sudoers with visudo
            
         Enable Auto-login
         Create File: nano /etc/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
         Insert Following into file:
         [SeatDefaults]
         greeter-session=lightdm-gtk-greeter
         autologin-user=username 
         autologin-user-timeout=0

            
            

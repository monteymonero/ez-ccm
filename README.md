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


 ### THINGS TO INSTALL:
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
### THINGS To ADJUST:

        EDIT THE SYSCTL.SYS        
        sudo nano /etc/sysctl.conf
        
### MAKING ADJUSTMENTS FOR BETTER PERFORMANCE UNDER LOAD ###        
############################################################

############# IMPROVMNETS FOR MEMORY MANAGEMENT ############
# The idea with making the canges is to free up RAM when there
# is a shortage either by trimming caches or swapping out memory.
############################################################

# Increase Maximum File Descriptors (FD) for entire system (DEFAULT is 97001)
# Maximum FD is enforced on a kernel level. It is cumulative system wide.
fs.file-max = 2097152

# Adjusts tendency of the OS to use swap (RANGE: 0 = prevent  100 = swap often)
vm.swappiness = 10

# Increases when applications are blocked from writing to the pagecache and
# must wait for kernel (background flusher threads) to reduce the amount of
# dirty memory.
# (DEFAULT is 20)
vm.dirty_ratio = 60

# Works along with "vm.dirty.ratio" to determine pagecache writeback behavior.
# When value is increased, more dirty memory is kept in the system for a longer time.
# If more dirty memory is allowed to persist in the system, a reduction to writeback
# I/O and an increased chance for optimal I/O patterns. However, more dirty memory
# can effect latency when memory needs to be reclaimed or at synchronization points
# when it needs to be written back to disk.
# (DEFAULT is 10)
vm.dirty_background_ratio = 2

# The amount of physical memory to keep in reserve to prevent OOM condition.
# (Setting depends on RAM installed)
vm.min_free_kbytes= 262144

# Adjust the when the OS reclaims swap space back to memory (DEFAULT 100)
vm.vfs_cache_pressure=50

### GENERAL NETWORK SECURITY OPTIONS ###

# Number of times SYNACKs for passive TCP connection.
net.ipv4.tcp_synack_retries = 2

# Allowed local port range
net.ipv4.ip_local_port_range = 2000 65535

# Protect Against TCP Time-Wait
net.ipv4.tcp_rfc1337 = 1

# Decrease the time default value for tcp_fin_timeout connection
net.ipv4.tcp_fin_timeout = 15

# Decrease the time default value for connections to keep alive
net.ipv4.tcp_keepalive_time = 300
net.ipv4.tcp_keepalive_probes = 5
net.ipv4.tcp_keepalive_intvl = 15

### TUNING NETWORK PERFORMANCE ###

# Default Socket Receive Buffer
net.core.rmem_default = 31457280

# Maximum Socket Receive Buffer
net.core.rmem_max = 12582912

# Default Socket Send Buffer
net.core.wmem_default = 31457280

# Maximum Socket Send Buffer
net.core.wmem_max = 12582912

# Increase number of incoming connections
net.core.somaxconn = 4096

# Increase number of incoming connections backlog
net.core.netdev_max_backlog = 65536

# Increase the maximum amount of option memory buffers
net.core.optmem_max = 25165824

# Increase the maximum total buffer-space allocatable
# This is measured in units of pages (4096 bytes)
net.ipv4.tcp_mem = 65536 131072 262144
net.ipv4.udp_mem = 65536 131072 262144

# Increase the read-buffer space allocatable
net.ipv4.tcp_rmem = 8192 87380 16777216
net.ipv4.udp_rmem_min = 16384

# Increase the write-buffer-space allocatable
net.ipv4.tcp_wmem = 8192 65536 16777216
net.ipv4.udp_wmem_min = 16384

# Increase the tcp-time-wait buckets pool size to prevent simple DOS attacks
net.ipv4.tcp_max_tw_buckets = 1440000
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_tw_reuse = 1




        vm.nr_hugepages=512



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

            
            

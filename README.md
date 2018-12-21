# INFO

This script enables the safe-shutdown and reset buttons on Retroflag's NesPi & SuperPi cases on OSMC and Raspbian, the fan also gets shutdown. It is basically a stripped down version of ES-generic-shutdown by cyperghost so all credit goes to him!

https://github.com/crcerror/ES-generic-shutdown  
http://retroflag.com/  

# 1. Download and compile raspi-gpio or use comand below:

Raspbian: 
sudo apt-get install raspi-gpio

OSMC:
cd /usr/src && wget https://github.com/Denisuu/OSMC_NesPi-SuperPi_Safe-Shutdown/raw/master/raspi-gpio-osmc.tar.gz && tar -xvzf raspi-gpio-osmc.tar.gz && cd /usr/src/raspi-gpio && sudo make install

# 2. Make directory & install shutdownscript:

mkdir /home/pi/scripts && cd /home/pi/scripts && wget https://raw.githubusercontent.com/Denisuu/OSMC_NesPi-SuperPi_Safe-Shutdown/master/multi_switch.sh && chmod +x multi_switch.sh

# 3a. Edit rc.local to autostart the script:

sudo nano /etc/rc.local

```
/home/osmc/scripts/multi_switch.sh --nespi+ & #Add this line above exit 0!
exit 0
```

# 4. Install fan_shutdown script (by cyperghost):

cd /lib/systemd/system-shutdown/ && sudo wget https://raw.githubusercontent.com/crcerror/ES-generic-shutdown/master/shutdown_fan && sudo chmod +x shutdown_fan

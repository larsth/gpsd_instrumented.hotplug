gpsd_instrumented.hotplug
=========================

gpsd_instrumented.hotplug is a /lib/udev/gpsd.hotplug file that is instrumented with logging statements.


How to use it
-------------

To use hotplug logging with gpsd:

    1. Get a copy of this repository (requires that the git command had been installed on your system):
        
        git clone https://github.com/larsth/gpsd_instrumented.hotplug
        
    2. Enter the directory (from the directory where you issued the above command):
    
        cd ./gpsd_instrumented.hotplug
        
    3. Copy the shell script to /lib/udev/ (but only if the file doesn´t exisists):
    
        if [ -n /lib/udev/gpsd_instrumented.hotplug] sudo cp ./gpsd_instrumented.hotplug /lib/udev/gpsd_instrumented.hotplug fi
        
    4. Change the owner to root, change the group to root, and change permissions:
    
        sudo chown root /lib/udev/gpsd_instrumented.hotplug && sudo chgrp root /lib/udev/gpsd_instrumented.hotplug && chown 554 /lib/udev/gpsd_instrumented.hotplug/lib/udev/gpsd_instrumented.hotplug
    
    5. Inside /lib/udev/rules.d find the gpsd rules file:
    
        ls /lib/udev/rules.d/*-gpsd.rules
        
    6. Now first create a backup:
    
        sudo cp /lib/udev/rules.d/N-gpsd.rules /root/lib_udev_rules.d_N-gpsd.rules;sync;sync
        - where you replace N with the *.rules file´s priority number.
        
    7. Edit the /lib/udev/rules.d/N-gpsd.rules file.
        Everywhere you want logging, replace:
        
            RUN+="/lib/udev/gpsd.hotplug"
            
            with:
            
            RUN+="/lib/udev/gpsd_instrumented.hotplug"
    

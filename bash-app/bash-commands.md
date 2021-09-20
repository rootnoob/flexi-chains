Base command:  
f-chains  

**add-chain** $name

**add-link** $chain $number  
Adds link number $number in the chain.  

**set-link** $chain $number $guard/tunnel  
Sets link to guard or tunnel.  

**edit-link** $chain $number 
    add-config  $file                                           #adds config file with $number sum+1  
    set-config-protocol $number $protocol                       #sets config protocol for config number $number      
    rm-config $number                                           #removes config number $number  
    set-mode $static/session,units,x,y/rswitch,units,x,y        #sets link mode  
    firewall                                                    #opens firewall conig file in nano  
    set-config-vm $number                                       #sets VM for config number $number  
    
**reboot-link** $chain $number  
#reboots link number $number  




    
    


    









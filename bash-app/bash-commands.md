Base command:  
fc guard

create [$guard-name] [guard-protocol] [$vm]
#This creates a guard. A directory is create titled guard-name and then flexi-chains does magic assigning the specific protocol and template, so all that is needed in the guard directory is to place a valid protocol configuration file, (i.e. net-tables), and the config file destination in the vm.

delete [$guard-name]

edit [$guard-name] [protocol{}] [$vm]


**Base command**
fc tunnel 

create [$tunnel-name] [protocol{}] [$vm]

delete [$tunnel-name]

edit [$tunnel-name] [protocol{}] [$vm]

**Base command**
fc chain 

create [$chain-name]

delete [$chain-name]

set-link [$chain-name] [$link-number] -type=[type{guard,tunnel}] -mode=[$link-mode]
if chain !exist:
error: chain does not exist
else:
    If link-number=1 OR link-number-1 exists in chain, then:
        if link-number exists in chain, then:
            verify input & assign variables
        else:
            verify input and require variables -type and -mode
    else:
        error: cannot set link $link-number before previous setting previous link(s)
        

fc chain launch [chain-name]
#for all links in chain, if(!=isChainActive()): start link; for all links except link(1) in chain, set netvm to link(link-1)
**add-chain** $name

**add-link** $chain $number  
Adds link number $number in the chain.  

**set-link** $chain $number $guard/tunnel  
Sets link to guard or tunnel.  

**edit-link** $chain $number  
    mode= $static, staticsession(mintime,maxtime) rotatesession(mintime,maxtime) randomsession(mintime,maxtime)        #sets link mode    
      
    
    
**reboot-link** $chain $number  
#reboots link number $number  




    
    


    









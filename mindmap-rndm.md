admin-client run program  
does admin-client run in dom0 or can we use a special adminVM? ask the forums.  

bash-client is simple to do (but beware input safety until V0.1)  
note to all: (beware safety & security of this project until V1.0 - I am currently a one man band with ltd time)  

barebones-gui is simple to do  

qubes-guardVM-client packages  
qubes-tunnelVM-client packages  
(the admin-client will recognise ANY and ALL vms tagged fc-guardVM/fc-tunnelVM, so do not mess about with this)  

iptables - literally just loading a config file which we'll force qubes to pickup (cba to do anything else right now)  
glider (literally just loading the config at runtime from the admin-client - yes, because I like to hack - u do a better job if u have the time ;)  



admin-client  
run the chain  
chain starts all the links you select (guardVMs, tunnelVMs - under the respective function (static, reboot, etc)  (static first lol, reboot etc later-on).  
then the config 'files' are just loaded in to the respective guardVMs/TunnelVMs everytime they are started (e.g. static, reboot, etc)  
because I'm super duper lazy, I will just set provides_network to 1 and set the netVM according to the link# (qubes makes my life so easy)  

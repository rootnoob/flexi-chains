<h1>Gen0 design abstract</h1>  

To get a working program running, gen0 will work by utilising existing projects.  
 


To keep it simple as possible, I shall describe what flexi-chains really is, at it's core (it's 'modules').  
<details>
  <summary>Flexi-chains is built atop [Qubes](https://qubes-os.org)</summary> 
The modules however could be further abstracted and adapted in the future to use a different compartmentalisation system - Qubes was chosen as it is open-source, has a strong community and is the most advanced that I can publicly build upon.  
</details>

Think of the abstraction simply, like this:  
| [0]  | (application layer) | Flexichain chains |
|------|---------------------|--------------|
| [-1] | (OS layer)          | Qubes        |

'Flexi'-'Chains' does what it says on the tin.  
Flexi-Chains is really just an interface for configuring 'flexible' 'chains.  

What is a **chain**?    
A chain is formed of **link(s)**.  
A link is either a **guard** or a **tunnel**.  

A **guard** could be an IPS,IDS, firewall.             
A **tunnel** could be openvpn, wireguard, socks proxy, etc.  
Although a chain is a sequence of links, a link could be part of many chains.  
For instance: I have a Guard Link which blocks all non-https traffic. I have multiple chains which use this guard link as the first link in the chain.  

Chains are flexible. Every link, sequentially numbered from 1, can be assigned a different mode. The modes are:  
Static  
SessionStatic(mintime,maxtime)  
#reboot the assigned guard/tunnel every random(mintime,maxtime) mins, if maxtime is not set then the session will be changed every mintime mins. This only works if the guards/tunnels assigned are not in use by any other chain.  
SessionRotate(mintime,maxtime)  
#change the link guard/tunnel every random(mintime,maxtime) mins, in the sequential order of the guards/tunnels attached to the link. If the guard/tunnel is in use by another chain at the end of the session, it won't be shutdown, otherwise it will be shutdown.  
SessionRandom(mintime,maxtime)  
#same as SessionRotate, except the next guard/tunnel is selected randomly from the list attached to the link. 

<h2>How does it work (example)?</h2>  

E.G:  
**fc guard create [$guard-name] [guard-protocol] [$vm]**  
#This creates a guard. A directory is create titled guard-name and then flexi-chains does magic assigning the specific protocol and template, so all that is needed in the guard directory is to place a valid protocol configuration file, (i.e. net-tables), and the config file destination in the vm.  

**fc guard delete [$guard-name]**  

**fc guard edit [$guard-name] [protocol{}] [$vm]**

**fc tunnel create [$tunnel-name] [protocol{}] [$vm]**  

**fc tunnel delete [$tunnel-name]**  

**fc tunnel edit [$tunnel-name] [protocol{}] [$vm]**

**fc chain -create [$chain-name]**  

**fc chain -delete [$chain-name]**  

**fc chain -set-link [$chain-name] [$link-number] [type{guard,tunnel}] [$link-mode]**       
#link-mode: STATIC, SessionSTATIC(min-time,max-time), sessionRotate(min-time,max-time), sessionRandom(min-time,max-time).  
#SessionRotate and SessionRandom allow multiple tunnels/guards to be assigned to a tunnel/guard link in a chain, and with rotate, the link will be replaced between min-time,max-time,with the next tunnel in the priority. For random, it is the same than rotate, other than you may have 50 configs and instead of being selected sequentially as with rotate, random just chooses any random one. HENCE THE NAME, FLEXI-CHAINS. Note: if the guard/tunnel is being used by another chain when using sessionRandom/SessionRotate the guard/tunnel will not be shutdown (as this would affect the other chain) upon session end.




**fc chain launch [chain-name]**  
#for all links in chain, if(!=isChainActive()): start link; for all links except link(1) in chain, set netvm to link(link-1)

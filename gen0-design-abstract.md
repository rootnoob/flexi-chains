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
  bbbbbbbbbbbbb
Although a chain is a sequence of links, a link could be part of many chains.  
For instance: I have a Guard Link which blocks all non-https traffic. I have multiple chains which use this guard link as the first link in the chain.  

<h2>How does it work (example)?</h2>  

E.G:  
**fc link -create [link-name] [guard/tunnel] [protocol] [template]**  
#Creates a link. The parameter protocol has different valid options depending on whether the link is guard or tunnel.
#For now, template

**fc link -delete [link-name]**

**fc chain -create [chain-name]**

**fc chain -set-link [chain-name] [link-number] [link-name]**       

**fc link -edit [link-name] [protocol] [template]** 

**fc chain -** everest 1 set-mode session -mins -10 -20    
#Sets link 1 in the chain, (our iptables firewall configured Guard), to reboot every 10-20 mins    

**fc edit-link** everest 1 set-config-vm 1 debminimal-disp    
#Flexi-chains will boot the debminimal-disp VM when config file 1 is chosen for link 1 in the everest chain 

**fc start-chain** everest  
#As configured above, this will launch all the link(s) configured (only 1), selecting the config (only the iptables firewallfirst.conf is added, so it will select that) - and launching the configured VM (debminimal-disp) for the selected config for the link(s). As we set the mode to session,mins,10,20 for this link (the only one), this link will reboot every 10-20 minutes (in effect the whole chain is rebooting as there's only 1 link in the chain).



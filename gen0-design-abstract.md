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

<h2>How does it work (example)?</h2>  

E.G:  
**fc guard create [$guard-name] [protocol{}] [$template]**  
#Protocol{} is one of the compatible protocols, for guard/tunnel respectively.
#Creates a link. The parameter protocol has different valid options depending on whether the link is guard or tunnel.
#For now, template

**fc guard delete [$guard-name]**  

**fc guard edit [$guard-name] [protocol{}] [$template]**

**fc tunnel create [$tunnel-name] [protocol{}] [$template]**  

**fc tunnel delete [$tunnel-name]**  

**fc tunnel edit [$tunnel-name] [protocol{}] [$template]**

**fc chain -create [$chain-name]**  

**fc chain -delete [$chain-name]**  

**fc chain -set-link [$chain-name] [$link-number] [type{guard,tunnel}] [$link-mode]**       
#link-mode: STATIC, SessionSTATIC(min-time,max-time), sessionRotate(min-time,max-time), sessionRandom(min-time,max-time).  
#SessionRotate and SessionRandom allow multiple tunnels/guards to be assigned to a tunnel/guard link in a chain, and with rotate, the link will be replaced between min-time,max-time,with the next tunnel in the priority. For random, it is the same than rotate, other than you may have 50 configs and instead of being selected sequentially as with rotate, random just chooses any random one. HENCE THE NAME, FLEXI-CHAINS. Note: if the guard/tunnel link is being used by another chain when using sessionRandom/SessionRotate the link will not be shutdown (as this would affect the other chain) upon session-link-change.




**fc chain launch [chain-name]**  
#As configured above, this will launch all the link(s) configured (only 1), selecting the config (only the iptables firewallfirst.conf is added, so it will select that) - and launching the configured VM (debminimal-disp) for the selected config for the link(s). As we set the mode to session,mins,10,20 for this link (the only one), this link will reboot every 10-20 minutes (in effect the whole chain is rebooting as there's only 1 link in the chain).



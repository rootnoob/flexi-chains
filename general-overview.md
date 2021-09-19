<h1>How it works - General Overview</h1>

<h2>Introduction - Key Concepts</h2>

Flexi-Chains enables you to create **chain**s.  
Each chain is composed of **link**s.  
Links are chronologically numbered integers i.e:  
link 1, link 2, link 3, etc...  

A link can be a **guard** or a **tunnel**.  
A guard is intended to act as a dedicated guard - (e.g. firewall, IPS/IDS).    
A tunnel is intended to tunnel/forward your traffic.  
FLexi-chains enables you to chain together an unlimited^ number of links - of guards and/or tunnels.  
Flexi-chains enables you to chain together any^^ tunnel protocol (openvpn, socks proxy, TOR, etc), in any order^^.  
Although there is much overlap, to simplify things - you should think of **guard**s and **tunnel**s as entirely different from one-another.  

Think of it like this:  
Link (1,2,3...)  
**Guard** / **Tunnel**  

<h2>Guard Links</h2>

A **guard** link has a guardVM and 

<details>
<summary>How this works</summary>
 
 Simply add the tag guardVM to any of your QubesVMs  
 To add a description simply  
</details>

<h2>Tunnel Links</h2>
 
<details>
<summary></summary>
</details>


^:  
Limited only by your system resources, and practical latency/bandwidth constraints.  
^^:  
Subject to availability & compatability  
Please also see: [Understanding TCP & UDP - and flexi-chains limits]()


<h2>Future Concepts</h2>

<details>
  <summary>Expand</summary>
</details>

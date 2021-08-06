|          Link<br>Info  | 1            | 2                          | 3                   | 4                   | 5                             | 6           | 7                           |
|------------------------|--------------|----------------------------|---------------------|---------------------|-------------------------------|-------------|-----------------------------|
| tunnel/guard           | guard        | tunnel                     | tunnel              | tunnel              | tunnel                        | guard       | tunnel                      |
| guardVM                | sys-firewall |                            |                     |                     |                               | mirage-disp |                             |
| tunnelVM(s)            |              | vpn-disp(*)                | proxy-disp(*)       | proxy-disp(*)       | vpn-disp(*)                   |             | sys-whonix(a),proxy-disp(*) |
| Tunnel Setting         |              | STATIC                     | session(mins,15,20) | session(mins,20,30) | switch(mins,10,20)            |             | STATIC                      |
| Config List            |              |                            |                     |                     |                               |             |                             |
| a                      |              | /mullvad/wireguard/eu.conf | /x/socks5/list.conf | /x/https/list.conf  | /nordvpn/wireguard/world.conf |             | TOR                         |
| b                      |              |                            |                     |                     | /mullvad/openVPN/USA.conf     |             | /resi/https/world.conf      |


<h3>Link</h3>

The link(s) form the chain. Links are un(limited - by latency and resource constraints). You configure each links.
Links can be tunnels/guards. (hops/firewalls;vpns/firewall).

<h3>Hop Setting</h3>

default=STATIC  
**STATIC**: The hop tunnel is unchanged after creating the chain.  
**session($time,$min,$max)**: The hop tunnel is restarted based on the time variables provided.  
This will restart the VM, and it will go through the same **initialisation process**.
$min is required.  
Setting $max means the session will last a duration=random($min,$max).  
$time is the unit seconds/mins/hours  
**switch($time,$min,$max)**



Notes:  
**Initialisation Process**  
Boot VM set for hop. 
Choose random entry from a random .conf file provided (from the config list for the hop). 

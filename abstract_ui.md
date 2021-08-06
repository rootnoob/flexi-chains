|          Hop<br>Info  | 1                          | 2                   | 3                   | 4                             | 5               |
|-----------------------|----------------------------|---------------------|---------------------|-------------------------------|-----------------|
| Hop Setting           | STATIC                     | session(mins,15,20) | session(mins,20,30) | switch(mins,10,20)            | STATIC          |
| Config List           | /mullvad/wireguard/eu.conf | /x/socks5/list.conf | /x/https/list.conf  | /nordvpn/wireguard/world.conf | tor(sys-whonix) |
| ''                    |                            |                     |                     | /mullvad/openVPN/USA.conf     |                 |


<h3>Hop</h3>

A hop is a link in the chain. Hops are un(limited - by latency and resource constraints). You configure each hope.

<h3>Hop Setting</h3>

default=STATIC  
**STATIC**: The connection is unchanged after creating the chain.
**session($time,$min,$max)**  
$min is required.  
Setting $max means the session will last a duration=random($min,$max).  
$time is the unit seconds/mins/hours  

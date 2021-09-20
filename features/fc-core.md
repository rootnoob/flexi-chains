**Chain**s


**Link**s:  
Guards | Tunnels


<h2>Guards</h2>

Master (admin-client)  
<details>
<summary>Slave (guardVM-client) </summary>

flexi-chains can work with any VM type/OS (including unikernels): provided there is a compatible guardVM client for said VM type/OS.
</details>
<details>
<summary>'mode'</summary>

STATIC  
REBOOT(0,TT,X,Y)  #(algorithm,timeunits,from,until)  
ROTATE(0,TT,X,Y)  #(algorithm,timeunits,from,until)

</details>
<details>
<summary>Config File(s)</summary>

firewall/ids/ips/etc config file format
</details>

<h2>Tunnels</h2>

Master (admin-client)  
<summary>Slave (tunnelVM-client) </summary>

flexi-chains can work with any VM type/OS (including unikernels): provided there is a compatible tunnelVM-client client for said VM type/OS.
</details>
<details>
<summary>'mode'</summary>

STATIC  
REBOOT(0,TT,X,Y)  #(algorithm,timeunits,from,until)  
ROTATE(0,TT,X,Y)  #(algorithm,timeunits,from,until)

</details>
<details>
<summary>Config File(s)</summary>

glider* config file format #*(gen0)
</details>

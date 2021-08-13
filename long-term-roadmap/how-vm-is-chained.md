<h2>How are VMs chained?</h2>

VMs are chained very simply by setting parameter 'provides_network' to '1'  
Then, for chains, setting the networkVM of link(number-1) to link(number)  
i.e: link 1 network VM is link 2 - link 2 network VM is link 3, etc.  


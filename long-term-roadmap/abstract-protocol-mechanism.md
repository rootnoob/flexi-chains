<h2>how flexic-chains works with multiple protocols</h2>  

FLexi-chains simply loads the config file into the program in the VM which handles the protocol.  

loadConfig(protocol,configfile):  
  if protocol.program present:  
      if configfile is valid for protocol:  
        load configfile into program in VM  
  else:  
    configfile error 'output'  
  else:  
    VM does not have 'protocol.program' for protocol  

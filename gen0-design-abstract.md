<h1>Gen0 design abstract</h1>  

To get a working program running, gen0 will work by utilising existing projects.  

Instead of writing a dedicated interface for each protocol/program I intend to initially write flexi-chains to work with [glider](https://github.com/nadoo/glider)  
(This will mean the licence will be restricted to GPL3 for gen0)  


To keep it simple as possible, I shall describe what flexi-chains really is, at it's core (it's 'modules').  

Flexi-chains is built atop Qubes  
The modules however could be further abstracted and adapted in the future to use a different compartmentalisation system - Qubes was chosen as it is open-source, has a strong community and is the most advanced that I can publicly build upon.  

Think of the abstraction simply, like this:  
[0] Flexi chains  
[-1 - OS layer] Qubes


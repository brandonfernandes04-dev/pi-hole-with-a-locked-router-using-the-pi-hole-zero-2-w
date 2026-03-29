# pi-hole with a locked router using the rasberry pi zero 2-w

# Materials Used or Needed if following along:

You will need at a minimum a rasberry pi zero, microSD card, and a 2.5A power supply. If you wish to do the install from the device itself. (Headed os as opposed to headless and sshing into from your main pc) Pick up the neccesarry adapters for you model of pi. If your using the zero 2 w like me this will include a micro USB A to MicroUSB adapter. As well as an hdmi to mini hdmi adapter. I mention this because when I purchased my kit from the link below I was given a micro sd with a headed version of ras pi OS already flashed to it. However the things I mentioned you would need were also inluded in the kit.  
Here is the site I ordered from! [rasberry pi zero 2 w](https://www.canakit.com/raspberry-pi-zero-2-w.html?srsltid=AfmBOoq6ZGVrahwmnbULeVIuAjeN4HNMOT22tkqwX1skWsml_CyOiQSV) In this case I went with starter kit which is the black case and the 32gb MicroSD. (This is relevant for any wishing to do this project as well because the heat sink given causes the case to not close all the way so if your following along consider buying a case with more verticle space.) 

# Prerequisites:

The First thing to check is exactly how much control over your router you have. The goodnews is there is a method for all levels of control. To begin find your routers gateway (The Ip address for your router) This will be available from a number of places the easiest is often just your phone. Once you have this number throw it into your browser of choice to navigate to your routers settings. (Note that some companies may have an app for you to use which you might need to access to allow remote access of the settings from your computer.) Once you are at the settings look to see if your DNS settings can be changed. If you are unable to set a new DNS then thats ok there will just be a few extra steps. If you can leave this tutorial now as you just need a normal pi hole install and will be fine with just the standard docs. Next check if your are able to turn DHCP off completely. If not that is fine there will just be extra steps. While your here at your router settings Go ahead an turn DHCPv4 Lease Time down to its lowest value if you can.

# Setup:

From here we are gonna do a normal pihole install making sure to follow all steps such as setting a static ip. Once you are at your pi-hole dashboard. (The place your directed to when you do something like: http://your-pi-hole-ip/admin) You need to follow some additional steps to make your pi-hole work for your locked router. First up go to your pi-hole dashboard and under settings>DHCP you will be able to set your pi-hole up as your DHCP server. Set it up so that your handing ip's out from x-x-x-2 up to x-x-x-99 (x's are place holders due to each router having a differnent IP range. Use your networks IP range) then set the gateway (your router IP) and the net mask. But before we save and apply were gonna go back our router settings and reserve two IP adresses as such x-x-x-252 and x-x-x-253 set these to mac addresses that don't exsist. Next find DHCP beggining address and Ending address. Set these to x-x-x-252 to x-x-x-253. This is a work around I found after some digging. It should allow you to effectivley stop your router from acting as your DHCP after saving those settings go to your pi-hole dashboard and save the DHCP settings you made before. Note that if you can fully turn of dhcp on your router then there is no reason to do this method described and you should do so at this point before saving the dhcp settings for your pi. Next From here you can set up unbound on your pihole following the normal installation proccess.

Please Note that this is not meant to explain the proccess of installing pi-hole as a whole but rather how to use pi-hole with a router that locks you out of your dns settings.

# Helpful Links: 

For a step by step video tutorial (That really helped me get this going) showing what I have explained go [here](https://www.youtube.com/watch?v=FnO5MiNGS7g)

For the pi-hole installation proccess go [here](https://pi-hole.net/)

For unbound installation go [here](https://docs.pi-hole.net/guides/dns/unbound/)
 

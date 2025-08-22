
<h1>Bind 9 Primary and secondary dns server</h1>
  
<h2>Description</h2>
Project consisting of a bind9 primary and secondary server connected to a cisco asa dmz interface. To check functionality i then connected a client machine to an internal interface and finally linked the asa to an external connecter to access the outside network.
<br />


<h2></h2>

- <b>Cisco CML 2.8</b> 
- <b>Bind9</b>
- <b>Ubuntu terminal</b>


<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
The topology we will be using <br/>

<img src="images/the topology 1.PNG" height="80%" width="80%"/>
<br />
<br />
Configure interfaces on asa firewall<br/>
<img src="images/create interfaces 2.PNG"     height="80%" width="80%"/>
<br />
 Configure the interfaces on the asa firewall while changing the security level
 of the dmz zone to 50 so the internal interface can ping the dmz.<br />
<br />
<br />
Create default route<br/>
<img src= "images/allow icmp 3.PNG"    height="80%" width="80%"/>
<br />
Because asa firewalls dont inspect icmp packets by default we have to modify the policy map
to inspect ismp.<br />
 <br />
 <br />
  Configure pat <br />
<img src= "images/pat static route 4.1.PNG"    height="80%" width="80%"/>
  <br />
  next we have to create a network object to configure pat to allow traffic to the outside network.
  We also need a default route to network traffic knows where to go for connectivity to the external network.<br />
  <br />
  <br />
 Set up basic network functions  <br/>
 <img src= "images/set netplan ip 5.PNG"    height="80%" width="80%"/>
 <br />
Now we are ready to set up the ubuntu machine. Modify the netplan
file to set up basic addresses for network connectivity to allow for updates 
and to install bind9.<br />
<br />
<br />
Download bind9<br/>
<img src=  "images/update ubuntu 6.PNG"   height="80%" width="80%"/>
<br /> 
 Before we install bind9 its best to make sure the operating system is updated 
using the sudo apt-get update command. Then use the 
"sudo apt install bind9 bind9utils bind9-doc -y"to install bind9.<br /> 
<br />
<br />
Change netplan<br/>
<img src= "images/netplan 8.PNG"    height="80%" width="80%"/>
 <br /> 
Now we need to change the dns server in the netplan file to use itself as the 
dns server because we have downloaded all the files we need.<br />
<br />
<br />
Named.conf.options<br/>
<img src=  "images/named.conf.options 9.PNG"   height="80%" width="80%"/>
<br />
This is the main file of bind 9 dns. First its good to have an acl for security 
reasons. This is also the file where you would add the dns forwarders and, allow queries.<br />
<br />
<br />
Named.conf.local<br /> 
<img src="images/named.conf.local 10.PNG" height="80%" width="80%"/>
<br />
This is were you declare diffrent zones for this example we have a forward
and reverse zone. For the reverse zone dns looks up an ip for right to left
so one half of the ip is here ans the other in the actual zone file.<br />
<br />
<br />
Stop resolving ipv6 <br /> 
<img src=  "images/defaults.named-ipv4-only.PNG"   height="80%" width="80%"/>
 !!next!!<br /> 
Here we are not using ipv6 at this time so we should go into the 
/etc/default/named file and allow only to resolve ipv4 address.
this will simplify the logs.<br />
<br />
<br />
Create zone file<br/>
<img src=  "images/db.local 11.PNG"   height="80%" width="80%"/>
 <br /> 
 The zone file is the main file for our dns zone. It consists of different timers
and different dns records.<br />
<br />
<br />
Configure reverse zone<br/>
<img src=  "images/reverse zone 12.PNG"   height="80%" width="80%"/>
<br /> 
This file is similar to the file above but instead of resolving domain names to ip
addresses it resolves ip addresses to domain names.<br />
<br />
<br />
Check funtionality<br/>
<img src=  "images/nslookup end.PNG"   height="80%" width="80%"/>
<br /> 
Finaly use nslookup to make sure you can resolve both forward and reverse dns queries.<br />
<br />
<br />
<p/>



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>


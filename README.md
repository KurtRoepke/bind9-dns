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
Launch the utility: <br/>
<img src="images/topology.PNG" height="80%" width="80%"/>
<br />
<br />
Select the disk:  <br/>
<img src="images/asa set interfaces 1.PNG"     height="80%" width="80%"/>
<br />
<br />
<img src= "images/icmp and default route 2.PNG"    height="80%" width="80%"/>
 <br />
 <br />
<img src= "images/set nat 3.PNG"    height="80%" width="80%"/>
<br />
<br />
Confirm your selection:  <br/>
<img src= "images/change hostname 4.PNG"    height="80%" width="80%"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src=  "images/download bind9 5.PNG"   height="80%" width="80%"/>
<br />
<br />
Sanitization complete:  <br/>
<img src= "images/set netplan 6.PNG"    height="80%" width="80%"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src=  "images/named.conf.options 7.PNG"   height="80%" width="80%"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

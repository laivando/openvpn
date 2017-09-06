NetNam OpenVPN setup guide

----
## Table of contents

[I. Mikrotik OpenVPN Server Configuration.](#openvpnserver)

[II. Windows as OpenVPN Client installation & Configuration.](#openvpnclient)
	
[III. NetNam OpenVPN topology.](#netnamvpn)
- [1. Topology](#topo)
- [2. BGP Configuration](#bgpconfig)
- [3. Config file for client](#clientconfigfile)

<a name="openvpnserver"></a>
## I. Mikrotik OpenVPN Server Configuration.
Connect to the Mikrotik using Winbox.  Goto the System —> Certificates:
![image](https://user-images.githubusercontent.com/31034437/30104784-d3313894-9320-11e7-994c-e29ec0242768.png)

Generate the master Certificate Authority (CA) certificate & key on cmd ( Windows - Run as adminnistrator) (https://openvpn.net/index.php/open-source/documentation/howto.html#pki)

Click on Import Button, then select the CA certificate file and Server certificate file (in my case, it is ca.crt, server.crt, server.key) and press Import:
![image](https://user-images.githubusercontent.com/31034437/30104927-37e213bc-9321-11e7-9339-41cbb71a44e9.png)

Next we need to create the pool for openvpn client, for this, goto the IP—->Pool:
![image](https://user-images.githubusercontent.com/31034437/30104949-5500eedc-9321-11e7-83cd-4bc8117a3091.png)

Create each pool of /30 subnet:
![image](https://user-images.githubusercontent.com/31034437/30104975-6d187936-9321-11e7-8cc1-abbc60b5260b.png)

Create the profile for openvpn client by selecting “Profiles” tab and click on + button:
![image](https://user-images.githubusercontent.com/31034437/30104997-82055ea4-9321-11e7-90ad-6ae9de5fb3e0.png)

Move over to the Secrets tab and click on the + button to create user for openvpn client:
![image](https://user-images.githubusercontent.com/31034437/30105029-98182db6-9321-11e7-84bd-03b5db74cf42.png)

Enable OpenVPN Service and Select Valid Certificate by moving to the Interface take and click on “OVPN Server“:
![image](https://user-images.githubusercontent.com/31034437/30105076-b2660ce2-9321-11e7-94f3-2d55eddbcbdc.png)



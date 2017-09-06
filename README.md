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
- Connect to the Mikrotik using Winbox.  Goto the System —> Certificates.
![image](https://user-images.githubusercontent.com/31034437/30104784-d3313894-9320-11e7-994c-e29ec0242768.png)

- Generate the master Certificate Authority (CA) certificate & key on cmd ( Windows - Run as adminnistrator) (https://openvpn.net/index.php/open-source/documentation/howto.html#pki)

- Click on Import Button, then select the CA certificate file and Server certificate file (in my case, it is ca.crt, server.crt, server.key) and press Import.

![image](https://user-images.githubusercontent.com/31034437/30104927-37e213bc-9321-11e7-9339-41cbb71a44e9.png)

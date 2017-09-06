NetNam OpenVPN setup guide

----
## Table of contents

[I. Mikrotik OpenVPN Server Configuration.](#openvpnserver)

[II. Windows as OpenVPN Client installation & Configuration.](#openvpnclient)
	
[III. NetNam OpenVPN topology.](#netnamvpn)
- [1. Topology](#topo)
- [2. BGP Configuration](#bgpconfig)
- [3. Config file for NetNam HCM client](#clientconfigfile)

<a name="openvpnserver"></a>
## I. Mikrotik OpenVPN Server Configuration.

- Connect to the Mikrotik using Winbox.  Goto the System —> Certificates.<br>
![image](https://user-images.githubusercontent.com/31034437/30104784-d3313894-9320-11e7-994c-e29ec0242768.png)

- Generate the master Certificate Authority (CA) certificate & key on cmd ( Windows - Run as adminnistrator) https://openvpn.net/index.php/open-source/documentation/howto.html#pki

- Click on Import Button, then select the CA certificate file and Server certificate file. In my case, it is ca.crt, server.crt, server.key) and press Import.<br>
![image](https://user-images.githubusercontent.com/31034437/30104927-37e213bc-9321-11e7-9339-41cbb71a44e9.png)

- Next we need to create the pool for openvpn client, for this, goto the IP—->Pool.<br>
![image](https://user-images.githubusercontent.com/31034437/30104949-5500eedc-9321-11e7-83cd-4bc8117a3091.png)

- Create each pool of /30 subnet.<br>
![image](https://user-images.githubusercontent.com/31034437/30104975-6d187936-9321-11e7-8cc1-abbc60b5260b.png)

- Create the profile for openvpn client by selecting “Profiles” tab and click on + button.<br>
![image](https://user-images.githubusercontent.com/31034437/30104997-82055ea4-9321-11e7-90ad-6ae9de5fb3e0.png)

- Move over to the Secrets tab and click on the + button to create user for openvpn client.<br>
![image](https://user-images.githubusercontent.com/31034437/30105029-98182db6-9321-11e7-84bd-03b5db74cf42.png)

- Enable OpenVPN Service and Select Valid Certificate by moving to the Interface take and click on "OVPN Server".<br>
![image](https://user-images.githubusercontent.com/31034437/30105076-b2660ce2-9321-11e7-94f3-2d55eddbcbdc.png)

<a name="openvpnclient"></a>
## II. Windows as OpenVPN Client installation & Configuration.

- Download free OpenVPN client for windows from https://openvpn.net/index.php/download/community-downloads.html, and install it. Once it’s installed, move to the openvpn directory (C:\Program Files\OpenVPN\config).<br>
![image](https://user-images.githubusercontent.com/31034437/30106299-2e07563c-9325-11e7-8c1f-798a5a037827.png)

- Edit file config. You can download file from this repo.<br>
![image](https://user-images.githubusercontent.com/31034437/30106330-4b419348-9325-11e7-8a2b-e18eb48b4d5e.png)

<a name="netnamvpn"></a>
## III. NetNam OpenVPN topology.

<a name="topo"></a>
### 1. Topology<br>
![image](https://user-images.githubusercontent.com/31034437/30106802-da27a452-9326-11e7-8986-c8b2914ff542.png)

<a name="bgpconfig"></a>
### 2. BGP Configuration

![image](https://user-images.githubusercontent.com/31034437/30106834-fa1b8062-9326-11e7-8bae-4e260fd8f40d.png)

![image](https://user-images.githubusercontent.com/31034437/30106854-0adc800e-9327-11e7-8fbf-ab818fb1a3e5.png)

<a name="clientconfigfile"></a>
### 3. Config file for NetNam HCM client

\## Start ##<br>
client<br>
dev tun<br>
proto tcp<br>

remote 115.79.63.41 1755<br>
remote 115.79.63.43 1755<br>
remote 115.79.57.120 1755<br>
remote 115.79.63.24 1755<br>
remote 115.79.57.122 1755<br>

nobind<br>
persist-key<br>

tls-client<br>
ca ca.crt<br>

ping 10<br>
verb 3<br>

cipher AES-256-CBC<br>
auth SHA1<br>
pull<br>

auth-user-pass<br>

route 10.0.0.0 255.0.0.0<br>
route 101.53.58.0 255.255.255.0<br>
route 172.20.3.0 255.255.255.0<br>
route 172.115.0.0 255.255.255.0<br>
route 172.117.0.0 255.255.255.0<br>
route 172.20.2.0 255.255.255.0<br>
route 172.20.1.0 255.255.255.0<br>
route 101.53.21.0 255.255.255.0<br>
route 115.79.58.17 255.255.255.255<br>
route 10.160.0.0 255.255.255.0<br>
route 101.53.2.0 255.255.255.0<br>
\## End ##

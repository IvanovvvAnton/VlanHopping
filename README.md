# VlanHopping


# Table of contents

- ["Description of the project"](#Description-of-the-project)
- ["Description of the attack"](#Description-of-the-attack)
- -  ["The principle of operation of the ARP protocol"](#The-principle-of-operation-of-the-ARP-protocol)
- -  ["Description"](#Description-of-the-attack)
- ["Description of the implementation platform"](#Description-of-the-implementation-platform)
- ["How to install PnetLab and add the ishare2 function"](#How-to-install-PnetLab-and-add-the-ishare2-function)
- - ["MobaXterm"](#MobaXterm)
- - ["Special command"](#In-the-command-line-of-the-Netlab-terminal-enter-the-command)
- - ["Download configuration"](#To-download-the-configuration-of-a-specific-device-you-need-to-register-the-following-commands)
- - ["Result"](#Next-go-to-the-laboratory-and-see-the-changes-in-the-equipment-selection-list-a-configuration-named-Huawei-will-be-available)
- ["Creating a network lab"](#Creating-a-network-lab)
- ["Router Setup"](#Router-Setup) 
- - ["VLAN"](#VLAN-Creation)
- - ["IP addresses"](#Assigning-IP-addresses-for-VLAN-data)
- - ["DHCP Server"](#Configuring-a-DHCP-server-for-a-VLAN)
- - ["NAT"](#Configuring-NAT-to-access-the-external-network)
- ["Switch Setup"](#Switch-Setup)
- - ["VLAN"](#Creating-a-VLAN)
- - ["Ports"](#Assigning-trunk-and-access-ports)
- ["Implementation of the attack"](#Implementation-of-the-attack)
- ["Protection methods"](#Protection-methods)
- ["Implementation of protection methods"](#Implementation-of-protection-methods)
- ["Authors"](#Authors)

# Description of the project
Modern information technologies are subject to an increasing number of attacks that pose a threat to the loss of data integrity and confidentiality. The urgency of the problem of network attacks, such as ARP-spoofing, is becoming increasingly critical in the context of the widespread use of local networks in various spheres of life.

ARP-spoofing is a form of attack based on changing the ARP protocol, which is responsible for matching logical IP addresses and physical MAC addresses of devices. During the attack, the attacker sends false ARP requests and responses, spoofing MAC addresses. This allows it to fake and redirect network traffic, which can lead to serious consequences such as interception of information, its substitution or disruption of the normal functioning of the network.

The purpose of this scientific work is to study ARP-spoofing attack scenarios in virtual local area networks created using the PnetLAB platform. Taking into account the urgency of the problem and the severity of its consequences, the main focus is on developing effective methods of protection against ARP spoofing attacks. The results of this study can serve as a basis for the development of security strategies and ensure resilience to such threats in virtual local area networks.

# Description of the attack
## The principle of operation of the ARP protocol
As you know, addressing on the Internet is a 32-bit sequence of 0 and 1, called IP addresses. But the direct communication between two devices on the network is carried out at the channel layer addresses (MAC addresses). So, to determine the correspondence between the logical address of the network layer (IP) and the physical address of the device (MAC), the ARP protocol (Address Resolution Protocol) is used

It performs the main functions: mapping IPv4 addresses and MAC address, as well as string a mapping table (arp table).

Here is an example of obtaining the physical address of a device using the ARP protocol, for a visual examination of vulnerabilities when using it. When it becomes necessary to create a connection between two network devices (PC-1 and PC-2), the device (PC-1) sends a packet with a broadcast address in order to find out the MAC address that belongs to a particular device (PC-2) and request to send a response. 
                
The receiving network device (PC-2), after accepting this packet, must compare the IP address with its own, and in case of a match, generate a response message, where its MAC address is indicated directly (the MAC address of the PC-2 device).

An example of such an interaction can be seen in the picture.

![screen-gif](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/67f715c8-8539-4b92-bc4e-978313fbe58d)

## Description  
ARP-spoofing is a cyberattack based on the impact on the transmission of ARP frames. During the attack, the attacker scans the network and substitutes MAC addresses. This allows him to fake and redirect network traffic, which leads to serious consequences, such as interception of information, its substitution or disruption of the normal functioning of the network.

Due to the fact that the ARP request contains a broadcast MAC address, any device in the broadcast segment can receive such an ARP frame. 
Therefore, an attack option arises – the implementation of a man-in-the-middle cyberattack by replacing the MAC address of the router port with the MAC address of the offending device in the ARP table of the victim's device.

![screen-gif](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/5c4cadbf-a2b7-4c7a-80d4-77ba2f0bd1bb)

Thus, all traffic coming from the user's device to the router will be redirected to the intruder's device, while unnoticed by the user himself.

# Description of the implementation platform 
The base of the PnetLAB platform will be used to build and implement an ARP spoofing attack. This platform provides opportunities for designing local area networks in online and offline modes, as well as building a network together in real time. When creating a project (online laboratory), the platform allows you to add devices from various manufacturers and configure them through the built-in console. In addition to the built-in console, there is an alternative to using third-party applications with a console, since it is possible to connect to each added device on the network using various protocols.

# How to install PnetLab and add the ishare2 function
First you need to go to the official website in the Download tab (https://pnetlab.com/pages/download ) and download the file with the .ova extension, then use virtual platforms (VMware, VirtualBox, etc.) to upload this file to the platform. The VMware virtual platform was used in this project. As a result, we get:

![photo_2024-04-05_15-54-34](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/f6856b56-ed53-42a5-a43e-ca86e5763537)

Next, use the ip address that the virtual machine shows to go to the website (for example http://192.168.15.155 ). Select the Login by Online Mode tab, using Sign Up we will create an account (for this we will enter the username, e-mail, and password).

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/9306e494-27ce-489b-b3b7-2ef497f7e955)

Then you will be taken to a workspace where you can create projects, as well as view projects of other users.

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/745c6c5c-5f5e-4d03-b2d6-b2254974a2f5)

The installation process can also be found on the official website (https://pnetlab.com/pages/documentation?slug=install-PNETlab ). 

## Ishare2

Initially, PnetLAB has a very limited number of devices to select and use, so it is necessary to download ishare2.

### MobaXterm

But for convenient editing and use of the Netlab console, we will make a remote connection via a third-party application. We used Mobaxterm (https://mobaxterm.mobatek.net/download.html)

MobaXterm is a program designed for remote administration of computers and servers. The all-in-one network application for remote work gives you a lot of advantages, for example, when using SSH to connect to a remote server, a graphical SFTP browser automatically opens for direct editing of your remotely located files.

To connect to Netlab, follow these steps.
In the upper panel of the main window, select the “Session” item and in the window that appears:
- Connection type: "SSH"
- Remote host: The IP address that you received to access PnetLAB
- Specify username: root 
- Port: leave unchanged
  
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/2d674860-f94c-47ca-8e5e-d73307331812)

This way we get remote access to the PnetLAB console

Let's go back to setting up ishare2. Full instructions for downloading this extension are available at the link:
https://github.com/ishare2-org/ishare2-cli?tab=readme-ov-file#quick-start-%F0%9F%9A%80

After installing share 2, you can find and select the necessary hardware and download it as follows:
### In the command line of the Netlab terminal, enter the command
(for example, it will download the Huawei configuration)
```
root@pnetlab:~# ishare2 search huawei
```
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/2c26befc-bea0-45bc-b71e-8efdb6e858ac)

After that, a list of available devices with the name Huawei will be displayed. 

### To download the configuration of a specific device you need to register the following commands:
(for example, Huawei configuration number 529 will be downloaded)
```
root@pnetlab:~# ishare2 pull qemu 529
```
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/ad1bf2e0-0cec-4612-aa4f-e1d10ab3b937)

The download of the corresponding configuration will begin
### After the download is finished a message will appear:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/70f2ac3e-2c80-4efc-9c63-53cfd31a246c)

### Next go to the laboratory and see the changes in the equipment selection list a configuration named Huawei will be available. 

Before:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/14c7fd2a-8087-4361-9a5d-afdf7bb8f9e6)

After:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/34fe1616-430a-41e7-afdc-dc8dfbb08ef3)"

There may also be a situation where when searching for a configuration via share 2, it will not be found. Therefore, there is a second way to add devices.

First, you need to find the configuration by following the link: https://drive.labhub.eu.org

After downloading the desired image, we need to upload it directly to Netlab. Let's also use Mobaxterm, When connecting to the console, we can see the file view on the left:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/520db192-a217-4ffe-b422-6f4a91d8c21d)

It is necessary to follow the path:
```
/opt/unetlab/addons/qemu/
```

And then by clicking anywhere in the window with the right mouse button to open the window:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/a0a60412-5d3a-4f92-93ad-7ac2f5a98980)

Using the "upload to current folder" item, we will upload the necessary configuration

# Creating a network lab
The built virtual laboratory in Netlab will look like this:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/9a2562e2-9a16-492f-b999-a2f9d84e88c0)

It includes the following equipment:

– gateway for connecting to an external network (Network)

!!! It is important that when using VMware, you must select Type (Management (Cloud0))

– Microtik 7.6 router (Router), can be loaded using ishare2 (described above).

– Cisco IOS L2 Switch (Switch) – download link https://upw.io/772/i86bi_linux_l2-adventerprisek9-ms.SSA.high_iron_20190423 (the addition of this device is described above)

– the intruder's computer running Linux (Ubuntu);

– the victim's computer running Linux (Ubuntu_victim);

These devices are already in Netlab.

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/886bf7e8-9547-4394-9433-66e02d87ae1b)

Let's download Ubuntu Server 20.04 and Ubuntu Desktop 20.04, as well as WireShark (it will be useful in the future)

Next, by selecting Docker.io , select the image file as shown below:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/3fb79ca6-dfd6-4961-ade1-17bd19a62d0f)

Next, we will configure the network equipment

To set up a router on it, you need to create two VLANs, and configure automatic distribution of IP addresses for devices that will be located in these VLANs
# Router Setup 
## VLAN Creation
```
interface vlan add name=vlan110 vlan-id=110 interface=ether2
interface vlan add name=vlan115 vlan-id=115 interface=ether2
```
## Assigning IP addresses for VLAN data
```
ip address add address=192.168.110.1/24 network=192.168.110.0 interface=vlan110
ip address add address=192.168.115.1/24 network=192.168.115.0 interface=vlan115
```
## Configuring a DHCP server for a VLAN
```
dhcp server interface vlan 110 address space 192.168.110.0/24 gateway 192.168.110.1 addresses 192.168.110.2-192.168.110.15
dhcp server interface vlan 115 address space 192.168.115.0/24 gateway 192.168.115.1 addresses 192.168.115.2-192.168.115.15
```
## Configuring NAT to access the external network
```
ip firewall nat add action=masquerade chain=srcnat out-interface=ether2 
```
As a result, we will get the configuration, in order to output it, you can use the command
```
/ export compact
```
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/5d7b1ffd-c9b7-4d09-b595-3b1bba4a9bb8)

# Switch Setup
To do this, you need to switch to privileged mode with the commands
```
>enable
#configure terminal
```
## Creating a VLAN
```
vlan 110
name pc
vlan 115
name trunk
```
## Assigning trunk and access ports
```
interface e0/0
switchport mode access
switchport access vlan 110
```
```
interface e0/2
switchport mode trunk
switchport encapsulation dot1q
switchport trunk native vlan 115
switchport trunk allowed vlan 110
```
Next, you need to save the configuration using the command
```
write
```
And to output the configuration, use the command
```
show run
```

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/2e5ac7cb-765e-4f19-9fee-5d273c9000d4)

# Implementation of the attack

First, let's check the receipt of IP addresses by devices, for this we will prescribe
```
ifconfig
```
And we'll see

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/2cc87e14-8910-42ac-8e5e-8c79be2c14d1)
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/2c76c7bd-9b2f-408b-9fc7-f9c9212c20b2)

The IP addresses have been successfully received.

Now download the ARP-SCAN tool on Ubuntu, for this you need:
```
sudo su apt install arp-scan
```

After successful download, enter the command
```
sudo arp-scan --interface=ether1 --localnet
```

Will see:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/dfe60790-3baa-408f-ad99-4904ad632f9b)

Next, let's look at the ARP table on the victim's computer:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/29115455-1cf4-45b7-91db-0c07ee2b563b)

The attack itself will be implemented using the arpspoof tool, in order to see how it is set, you can write:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/077458d5-b178-4e53-93bb-8d574b34b0b0)

The next step will be to start the spoofing itself, for this we will prescribe
```
arpspoof -i eth1 -t 192.168.50.4 192.168.50.1
```

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/c58677a1-e490-4b6a-85c5-bcf2f08f5970)

We see that the attack was successful

Now let's check the ARP table on the victim's computer and see that the MAC addresses match. Thus, it can be concluded that the router's MAC address was successfully replaced with the physical address of the intruder's device. The Wireshark program was used to check traffic redirection:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/f5d77446-a35b-4b71-b22c-b575ed6bc895)

The figure shows that traffic coming from the Ubuntu_victim device (IP address 192.168.50.4/24) is redirected to a device with a MAC address 50:00:00:37:00:01, which corresponds to the offending Ubuntu device.

# Protection methods
There are several possible ways to protect against ARP-spoofing attacks:
1. Static ARP tables (You can statically assign all MAC addresses on the network to the corresponding IP addresses. This is very effective in preventing ARP poisoning, but requires a lot of work). 
2. Switch protection. Most managed switches are equipped with the functions of preventing cyber attacks ARP-spoofing, Dynamic ARP Inspection (DAI) - will be described further.
3. Physical protection (Proper control of physical access to the user's workplace, as well as control of unauthorized access to equipment, will also help prevent ARP-spoofing attacks).
4. Network isolation (It is necessary to segment the network, you can concentrate the most important resources in a specially allocated segment with stricter protection systems).

# Implementation of protection methods
Protection methods such as DHCP Snooping and DAI have been configured. 

DHCP Snooping protects your network from spoofing the DHCP server. Trusted ports are manually configured on the switches, and we will also set the specified number of packets that can pass through this port:
```
interface e0/0
ip dhcp snooping trust
ip dhcp snooping limit rate 100
```

As a result, we get:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/a872f34c-a79c-4ba4-ae40-b6c0d03c9a8c)

Now let's turn on DHCP Snooping for this we will prescribe:
```
ip dhcp snooping trust
ip dhcp snooping vlan 110, 115
```

As a result, we get:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/d95a521c-8f66-4913-8c17-492cc452ecaa)

We will also set up DAI, for this we will prescribe:
```
ip arp inspection vlan 110, 115
```

We will also assign this function to the ports using the command:
```
ip arp inspection trust
```

As a result, after re-implementing the attack, you can see that the MAC addresses in the ARP table do not change, and the switch recognizes the cyberattack, which indicates the successful implementation of protection methods

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/41a19b4b-1b0a-4da7-a7d7-a85143f49286)

# Authors
If you have any questions, you can ask them to us by writing to us at email:
- ivanovvvvvvvanton3829@gmail.com
- annakisel8534@gmail.com


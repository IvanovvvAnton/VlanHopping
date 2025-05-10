# 🌐🔄 VlanHopping

# 📚 Table of contents

## 📋 Table of Contents  
1. [💡 Introduction](#-introduction)  
   - [📚 Relevance of the study](#-relevance-of-the-study)  
   - [🔬 Object and subject of research](#-object-and-subject-of-research)  
   - [🎯 Purpose and objectives of the work](#-purpose-and-objectives-of-the-work)  
   - [🧠 Scientific novelty and practical significance](#-scientific-novelty-and-practical-significance)  

2. [🛠️ The structure of the work](#-the-structure-of-the-work)  

3. [🛠️ How to install PnetLab and add the ishare2 function](#-how-to-install-pnetlab-and-add-the-ishare2-function)  

4. [⚙️ Ishare2](#-ishare2)  
   - [🖥️ MobaXterm](#-mobaxterm)  

5. [🖧 Creating a network lab](#-creating-a-network-lab)  

6. [🔧 Router Setup](#-router-setup)  
   - [🔄 VLAN Creation](#-vlan-creation)  
   - [🔢 Assigning IP addresses for VLAN data](#-assigning-ip-addresses-for-vlan-data)  
   - [📡 Configuring a DHCP server for a VLAN](#-configuring-a-dhcp-server-for-a-vlan)  
   - [🔐 Configuring NAT to access the external network](#-configuring-nat-to-access-the-external-network)  

7. [🔌 Switch Setup](#-switch-setup)  
   - [🏷️ Creating a VLAN](#-creating-a-vlan)  
   - [🔀 Assigning trunk and access ports](#-assigning-trunk-and-access-ports)  

8. [💻 Implementation of the attack](#-implementation-of-the-attack)  
   - [🔍 Checking the status of the switch port status](#-checking-the-status-of-the-switch-port-status)  
   - [💥 Attack](#-attack)  
     - [⚡ Step 1: Install Yersinia](#-step-1-install-yersinia)  
     - [🔓 Step 2: Launch Yersinia in Graphical mode](#-step-2-launch-yersinia-in-graphical-mode)  
     - [⚙️ Step 3: Choosing an attack on the DTP protocol](#-step-3-choosing-an-attack-on-the-dtp-protocol)  
     - [🏁 Step 4: Launch the attack and verify success](#-step-4-launch-the-attack-and-verify-success)  

9. [🛡️ Protection methods](#-protection-methods)  

10. [📝 Conclusion](#-conclusion)  

11. [📝 Authors](#-authors) 

## 💡 Introduction
### 📚 Relevance of the study

In the context of the active introduction of virtualization technologies and increasing information security requirements, logical network segmentation methods are becoming particularly important. One of these technologies is VLAN (Virtual Local Area Network), a mechanism that allows you to logically divide devices connected to the same physical network into different virtual segments. This provides flexibility in network design, improves manageability, and enhances information security by isolating traffic.

However, despite its advantages, VLAN technology is subject to certain vulnerabilities that can be exploited by hackers to gain unauthorized access to information. One of these attacks is the VLAN hopping cyberattack, which allows an intruder to bypass segmentation restrictions and gain access to traffic transmitted on other VLANs. This threat is especially dangerous for corporate and government networks, where information security is of critical importance.

With the increasing use of VLANs in organizations of various fields, there is also an increasing interest in studying the vulnerabilities associated with this technology. Investigating the mechanisms of a VLAN hopping attack and ways to prevent it is becoming an important step in ensuring the integrity and confidentiality of network communications.

### 🔬 Object and subject of research

The object of the research is the technology of virtual local area networks (VLAN) used in corporate and educational local area networks.

The subject of the study is the implementation mechanisms of the VLAN hopping cyberattack, its impact on the security of the network infrastructure, as well as protection methods aimed at preventing such attacks.

### 🎯 Purpose and objectives of the work

The purpose of the study is to study the principles of implementing a VLAN hopping cyberattack, simulate this attack in a virtual laboratory, as well as analyze and implement measures to protect the network infrastructure from this threat.

To achieve this goal, it is necessary to solve the following tasks::

1 To study the theoretical foundations of VLAN and DTP protocol operation.

2 To build a network topology in a Netlab virtual laboratory using Cisco, Mikrotik devices and computers with various operating systems.

3 Implement a VLAN hopping cyberattack using specialized software.

4 Analyze the results of the attack and identify vulnerable elements of the network infrastructure.

5 Investigate and implement practical protection measures against VLAN hopping.

6 Evaluate the effectiveness of the proposed measures in terms of improving network security.

### 🧠 Scientific novelty and practical significance

The scientific novelty of the research lies in the practical modeling of a VLAN hopping cyberattack in a controlled virtual environment using open software solutions and the subsequent analysis of the effectiveness of protection methods.

The practical significance lies in the fact that the results can be applied in educational processes to train information security specialists, as well as used in real organizations to increase the resilience of network infrastructure to attacks of this kind.

## 🛠️ The structure of the work

The work consists of an introduction, three sections, a conclusion, and appendices. The first section discusses the theoretical foundations of VLAN technology and the DTP protocol, as well as a description of the VLAN hopping cyberattack vector. The second section presents the construction of a laboratory stand and a step-by-step implementation of the attack using the Yersinia utility. The third section contains an analysis of the results and a description of the methods of protection against VLAN hopping. In conclusion, the results of the study are summarized and recommendations are formulated.

### 🛠️How to install PnetLab and add the ishare2 function
First you need to go to the official website in the Download tab (https://pnetlab.com/pages/download ) and download the file with the .ova extension, then use virtual platforms (VMware, VirtualBox, etc.) to upload this file to the platform. The VMware virtual platform was used in this project. As a result, we get:

![photo_2024-04-05_15-54-34](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/f6856b56-ed53-42a5-a43e-ca86e5763537)

Next, use the ip address that the virtual machine shows to go to the website (for example http://192.168.15.155 ). Select the Login by Online Mode tab, using Sign Up we will create an account (for this we will enter the username, e-mail, and password).

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/9306e494-27ce-489b-b3b7-2ef497f7e955)

Then you will be taken to a workspace where you can create projects, as well as view projects of other users.

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/745c6c5c-5f5e-4d03-b2d6-b2254974a2f5)

The installation process can also be found on the official website (https://pnetlab.com/pages/documentation?slug=install-PNETlab ). 

## ⚙️ Ishare2

Initially, PnetLAB has a very limited number of devices to select and use, so it is necessary to download ishare2.

### 🖥️ MobaXterm

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

### 💡 In the command line of the Netlab terminal, enter the command

(for example, it will download the Huawei configuration)
```
root@pnetlab:~# ishare2 search huawei
```
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/2c26befc-bea0-45bc-b71e-8efdb6e858ac)

After that, a list of available devices with the name Huawei will be displayed. 

### 🔽 To download the configuration of a specific device you need to register the following commands:

(for example, Huawei configuration number 529 will be downloaded)
```
root@pnetlab:~# ishare2 pull qemu 529
```
![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/ad1bf2e0-0cec-4612-aa4f-e1d10ab3b937)

The download of the corresponding configuration will begin

After the download is finished a message will appear:

![image](https://github.com/AntonAndAnna/Arp-spoofing/assets/103459290/70f2ac3e-2c80-4efc-9c63-53cfd31a246c)

Next go to the laboratory and see the changes in the equipment selection list a configuration named Huawei will be available. 

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

# 🖧 Creating a network lab
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

# 🔧 Router Setup 
## 🔄 VLAN Creation
```
interface vlan add name=vlan50 vlan-id=50 interface=ether2
interface vlan add name=vlan55 vlan-id=55 interface=ether2
```
## 🔢 Assigning IP addresses for VLAN data
```
ip address add address=192.168.50.1/24 network=192.168.50.0 interface=vlan50
ip address add address=192.168.55.1/24 network=192.168.55.0 interface=vlan55
```
## 📡 Configuring a DHCP server for a VLAN
```
dhcp server interface vlan 50 address space 192.168.50.0/24 gateway 192.168.50.1 addresses 192.168.50.2-192.168.50.100
dhcp server interface vlan 55 address space 192.168.55.0/24 gateway 192.168.55.1 addresses 192.168.55.2-192.168.55.100
```
## 🔐 Configuring NAT to access the external network
```
ip firewall nat add action=masquerade chain=srcnat out-interface=ether2 
```
As a result, we will get the configuration, in order to output it, you can use the command
```
/ export compact
```
![image](https://github.com/user-attachments/assets/6012eedc-bf5c-406e-ad7b-f9922dc95bdd)

# 🔌 Switch Setup
To do this, you need to switch to privileged mode with the commands
```
>enable
#configure terminal
```
## 🏷️ Creating a VLAN
```
vlan 50
name work
vlan 55
name killer
```
## 🔀 Assigning trunk and access ports
```
interface e0/0
switchport mode trunk
switchport encapsulation dot1q
```
```
interface e0/1
switchport mode access
switchport access vlan 50
```
```
interface e0/2
switchport mode access
switchport access vlan 50
```
```
interface e0/3
switchport mode access
switchport access vlan 55
```
Next, you need to save the configuration using the command
```
write
```
And to output the configuration, use the command
```
show run
```

![image](https://github.com/user-attachments/assets/7a52f45e-8f3c-41ed-b247-e3cd29d95044)

# 💻 Implementation of the attack

First, let's check the receipt of IP addresses by devices, for this we will prescribe
```
ifconfig
```
And we'll see

![image](https://github.com/user-attachments/assets/87d3a9ba-cd40-446b-8c95-08c77d72a8a9)
![image](https://github.com/user-attachments/assets/1ff076e5-b8f0-43c0-a12a-e93a3d3ec6b1)

The IP addresses have been successfully received.

Then use 
```
show vlan brief
```
And see:

![image](https://github.com/user-attachments/assets/e2a11b57-bec9-49c7-92db-833948b89bd7)

### 🔍 Checking the status of the switch port status

To successfully implement a VLAN hopping cyberattack, it is important to determine the current status of the switch port to which the potential intruder's device is connected. In particular, it is necessary to check whether this port is in a mode that allows the automatic installation of a trunk connection, which can be used for embedding into other VLANs.

In Cisco technology, switches use the DTP (Dynamic Trunking Protocol) protocol to automatically negotiate the port mode. The port can be in one of the following modes:

- The access port belongs to only one VLAN and does not allow traffic from other VLANs to pass through;

- The trunk port transmits traffic from several VLANs at once, identifying them using tags;

- Dynamic desirable — the port is actively trying to establish a trunk connection if another port that supports DTP is connected to it;

- Dynamic auto — the port passively waits for an offer to install a trunk from the opposite device.

To determine the current mode, use the command (on Cisco IOS hardware):

```
show interfaces e0/3 switchport
```

Output example:

![image](https://github.com/user-attachments/assets/048b3b97-d726-4401-844f-ebf9f691e820)

To debug and view incoming RTP packets on a Cisco switch, you can use the debug rtp packet command. This command allows you to display detailed information about the process of exchanging DTP messages between the switch and the devices connected to the ports. By enabling debugging, the administrator can track which DTP packets are received on the ports and at what point their mode changes, which is useful for detecting VLAN hopping attack attempts.

![image](https://github.com/user-attachments/assets/481e0829-e7a2-4bd3-b52e-6554da7cf0e5)

## 💥 Attack

To implement a VLAN hopping attack using the Yersinia utility in graphical mode, several steps must be followed. Yersinia is a powerful utility for testing and exploiting vulnerabilities in network protocols, which provides a user—friendly interface for dealing with various types of attacks, including vulnerabilities in the DTP (Dynamic Trunking Protocol) protocol.

### ⚡Step 1: Install Yersinia

To install Yersinia on a Linux system, run the following commands:
```
sudo apt update
sudo apt install yersinia
```

### 🔓 Step 2: Launch Yersinia in Graphical mode

After installing Yersinia, you can run it in the graphical interface, which greatly facilitates the process of configuring and monitoring the attack. To do this, run the following command:

```
sudo -E yersinia -G
```

The team runs Yersinia with a graphical interface, allowing you to use a user-friendly GUI to set up attacks. The -E option launches the utility with superuser rights, and -G indicates launch in graphical mode.

After executing this command, the Yersinia graphical window opens, in which you can configure the attack, select the target network protocol and start exploiting vulnerabilities.

### ⚙️ Step 3: Choosing an attack on the DTP protocol

![image](https://github.com/user-attachments/assets/2a9fac62-90b8-45dd-ad9f-980ad2981af5)

### 🏁 Step 4: We launch the attack and see that it was successful

![image](https://github.com/user-attachments/assets/20a2594d-d6d7-42d7-9c5d-8d6ec90547d8)

When the VLAN hopping attack is successfully implemented using the Yersinia utility, the Cisco switch can detect a port configuration change and issue appropriate alerts about events. This is because the attack involves changing the status of the port, which can lead to the opening of a communication channel between different VLANs. Cisco switches use various mechanisms to monitor and respond to network anomalies, such as port configuration changes.

![image](https://github.com/user-attachments/assets/e007b030-4b50-4f0e-be7f-d27640a36550)

After the VLAN hopping attack is successfully implemented and the port configuration is changed, the device that was originally in VLAN 55 is no longer displayed in the corresponding table. This may mean that the attacker was able to redirect traffic or connect to another VLAN, thus "removing" the device from VLAN 55. As a result, the VLAN table shows that there are no devices in this segment, although it was previously registered, which confirms successful intervention and manipulation of network settings.

![image](https://github.com/user-attachments/assets/d7902f7f-8f8e-4920-88e2-8016e8029470)

![image](https://github.com/user-attachments/assets/b28eeeb6-7941-448a-b5e0-c348bde495d7)

To further implement the attack, the intruder adds a new VLAN interface on his device using the command
```
vconfig add eth1 50
```
to create a virtual interface with the VLAN ID 50. Then, using the command
```
ifconfig eth1.50 192.168.50.50 up
```
it assigns to this interface an IP address corresponding to VLAN 50. Thus, the intruder's device now has access to the VLAN segment 50, which allows it to exchange data with other devices on this VLAN and continue the attack, for example, using the "man in the middle" method.

![image](https://github.com/user-attachments/assets/faf821dc-1735-43a0-96f9-4a72252c39f8)

Check:

![image](https://github.com/user-attachments/assets/c4c194ad-8c8d-4793-893a-97aa1f97392a)

After adding the VLAN 50 interface and assigning the appropriate IP address, the intruder's device successfully jumps to another VLAN, in this case VLAN 50. This allows him to bypass network segmentation restrictions and gain access to resources located on this VLAN, including devices such as Ubuntu_work. Thus, the intruder can continue his actions, including intercepting traffic and interfering with network interactions between segments.

![image](https://github.com/user-attachments/assets/f68cd290-d23a-4975-a59b-840a9533541c)

## 🛡️ Protection methods

1 To protect against VLAN hopping attacks related to DTP protocol vulnerabilities, an important step is to disable this protocol on switch ports that should not be involved in automatic trunk configuration. To do this, use the switchport nonegotiate command.

The switchport nonegotiate command disables the ability to automatically negotiate tanks with another device, which prevents the use of the DTP protocol to dynamically configure a trunk connection. As a result, the port will not attempt to establish a trunk connection with another device, even if it supports DTP. This significantly reduces the likelihood that an attacker will be able to exploit the DTP vulnerability to bypass segmentation and switch to other VLANs.

To apply this command, follow these steps on the switch:
```
configure terminal
interface e0/0
switchport nonegotiate
```

![image](https://github.com/user-attachments/assets/050ef230-4387-4f22-b182-a8b00c6391ac)

2 VLAN 1 is a standard VLAN that is used by default on most network devices, such as Cisco switches, for various network functions, including management and data exchange protocols. This VLAN often remains active on all switch ports, which makes it vulnerable to attacks, as attackers may try to use it to bypass network segmentation.

3 All unused ports should be moved to a separate dedicated VLAN. Unused ports on the switch left in standard VLANs can be used by intruders to gain unauthorized access to the network. To minimize this risk, inactive ports should be moved to an isolated, dedicated VLAN, such as VLAN 999 or another specifically designated for unused ports.

![image](https://github.com/user-attachments/assets/9110e48c-91d2-4f2d-9a07-b1bc59c7b43e)

4 To increase network security, it is recommended to disable all unused ports on the switch to prevent intruders from using them to connect unauthorized devices. Disabling inactive ports helps reduce potential attack vectors, such as attacks using unregistered devices.

![image](https://github.com/user-attachments/assets/28714742-88ea-46bf-ab0e-c20d496a9ab3)

## 📝 Conclusion

During the research and implementation of the VLAN hopping cyberattack, it was demonstrated how vulnerabilities in VLAN technology, in particular the DTP protocol, can be used to bypass network segmentation and gain access to data from other VLANs. We have shown how an attacker, using a vulnerability in the DTP protocol, can gain the ability to transfer traffic between network segments, leading to risks of data interception and possible man-in-the-middle attacks.

To prevent such attacks, several effective protection methods were considered, including disabling the DTP protocol, not using VLAN 1, and transferring all unused ports to isolated VLANs with their subsequent disconnection. All these measures are aimed at improving network security, reducing possible vulnerability points and improving access control to various network segments.

Thus, to effectively protect against VLAN hopping cyber attacks and other threats related to incorrect VLAN configuration, it is necessary to apply an integrated approach, including regular checking and updating of network equipment configuration, the use of modern monitoring tools and protection against unauthorized access. The implementation of the proposed protection methods significantly increases the level of security and resilience of the network infrastructure to potential threats.

# Authors
If you have any questions, you can ask them to us by writing to us at email:
- ivanovvvvvvvanton3829@gmail.com
- annakisel8534@gmail.com


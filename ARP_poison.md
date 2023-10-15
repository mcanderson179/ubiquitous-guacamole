ARP (Address Resolution Protocol) poisoning, also known as ARP spoofing, is a network attack technique used to manipulate the ARP cache of devices on a local area network (LAN). ARP is responsible for mapping IP addresses to MAC addresses, allowing devices to communicate with each other on a local network. ARP poisoning occurs when an attacker sends malicious ARP packets to a target device or multiple devices, leading them to associate the attacker's MAC address with the IP address of a legitimate device on the network.

Using a pfsense firewall VM as a router, I built my network. Here is an illustration of my virtual network:
<img width="602" alt="Screenshot 2023-10-14 at 10 00 09 PM" src="https://github.com/mcanderson179/ubiquitous-guacamole/assets/90523886/7bd909a4-7b34-44d3-bf22-6dd576e2d06a">

The mac address of my pfsense firewall VM is 56-f3-7d-42-59-2e

The mac address of my Kali VM is 76-a1-45-41-2f-dd

I first checked the arp table on my Windows VM to check the mac addresses associated with the ip addresses the machine
<img width="483" alt="Screenshot 2023-10-14 at 9 38 47 PM" src="https://github.com/mcanderson179/ubiquitous-guacamole/assets/90523886/26ddf569-46a9-4219-b8c7-91079510b32f">

I then flooded the Windows machine with arp packets from my Kali VM.
<img width="869" alt="Screenshot 2023-10-14 at 9 52 44 PM" src="https://github.com/mcanderson179/ubiquitous-guacamole/assets/90523886/05946ce0-918d-415d-a7dc-51143a3b792f">

I then checked the arp table again. As you can see, the mac address for the router has changed to that of the Kali machine.
<img width="499" alt="Screenshot 2023-10-14 at 9 47 17 PM" src="https://github.com/mcanderson179/ubiquitous-guacamole/assets/90523886/0de9e611-68d7-4f84-b8a6-ea354958d857">


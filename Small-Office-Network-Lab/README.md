# Small Office Network Lab with SSH and Traffic Analysis

## Project Overview
This project demonstrates a small office network built with Cisco Packet Tracer and a live virtual lab using Oracle VirtualBox, PuTTY, and Wireshark.

I used Packet Tracer to design and test the logical network topology. I used VirtualBox to deploy an Ubuntu Server virtual machine, PuTTY to connect to it over SSH, and Wireshark to capture and analyze live network traffic.

This lab helped me practice network setup, IP addressing, remote administration, packet analysis, and troubleshooting.

## Tools Used
- Cisco Packet Tracer
- Oracle VirtualBox
- Ubuntu Server
- PuTTY
- Wireshark

## Project Goals
- Build a simple office LAN in Packet Tracer
- Configure IP addressing
- Set up an Ubuntu Server VM
- Enable SSH access
- Remotely connect using PuTTY
- Capture ICMP and SSH traffic in Wireshark
- Document errors and fixes

## Network Topology
### Packet Tracer Devices
- 1 Router
- 1 Switch
- 1 Server
- 2 PCs
<img width="964" height="751" alt="01-topology" src="https://github.com/user-attachments/assets/08e609d4-5903-478a-872e-9875402d35a0" />

### IP Addressing Plan
- Router: 192.168.10.1/24
- Server: 192.168.10.10/24
- PC1: 192.168.10.11/24
- PC2: 192.168.10.12/24
- Default Gateway: 192.168.10.1
<img width="703" height="712" alt="02-ip-config" src="https://github.com/user-attachments/assets/d0f62d35-e04e-4611-9da1-ed81142efb9e" />

## What I Did
### Phase 1: Packet Tracer Network Build
- Created a small office topology with a router, switch, server, and 2 PCs
- Connected all devices using straight-through cables
- Configured IPv4 addresses on the end devices
- Configured the router interface as the default gateway
- Tested connectivity with ping
<img width="700" height="713" alt="03-ping-test" src="https://github.com/user-attachments/assets/c1ea9063-64ec-4430-b707-35e307ddd90c" />

### Phase 2: VirtualBox Live Lab
- Created an Ubuntu Server virtual machine in Oracle VirtualBox
- Configured the VM to use a host-only adapter
- Verified the VM IP address using `ip a`
- Installed and started OpenSSH Server
<img width="785" height="519" alt="04-virutalbox-netowrk2" src="https://github.com/user-attachments/assets/85399fe0-cab0-4fbb-892d-c3cd594f6e6a" />
<img width="783" height="522" alt="04-virutalbox-network1" src="https://github.com/user-attachments/assets/ea358fe0-489e-4f1b-99ec-03f05052bbef" />
<img width="1285" height="889" alt="08-ubuntu-ip-a" src="https://github.com/user-attachments/assets/93f00a67-e814-4228-95ca-5a07769ecc4f" />

### Phase 3: Remote Access with PuTTY
- Used PuTTY to connect to the Ubuntu Server over SSH
- Verified remote access by running basic Linux commands
<img width="729" height="485" alt="05-putty-ssh-login" src="https://github.com/user-attachments/assets/575bb450-bfdc-47da-8988-b8563f285b0b" />

### Phase 4: Traffic Capture with Wireshark
- Captured ICMP traffic during ping tests
- Captured SSH traffic during the PuTTY session
- Applied display filters:
  - `icmp`
  - `tcp.port == 22`
- Saved the packet capture file for analysis
<img width="827" height="652" alt="06-wireshark-icmp" src="https://github.com/user-attachments/assets/46faf6a5-b994-4799-aba6-c21038a7f77c" />
<img width="779" height="592" alt="07-wireshark-ssh" src="https://github.com/user-attachments/assets/62847f4f-9ac5-48a9-b641-037afbb06eb7" />

## Commands Used
### Router Configuration
enable
configure terminal
interface gigabitEthernet0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
end
write memory

### Error: Wireshark not capturing SSH traffic

- Issue: Wireshark showed no packets when filtering for `tcp.port == 22`
- Cause: Capturing on the wrong network interface (Ethernet instead of VirtualBox adapter)
- Fix:
  - Cleared the filter
  - Selected the correct VirtualBox Host-Only adapter
  - Reconnected using PuTTY to generate traffic
  - Reapplied the filter after capture

<img width="781" height="595" alt="image_2026-04-19_213809885" src="https://github.com/user-attachments/assets/7f9050d0-e72f-4b9c-a35d-6b2cbeda0e0f" />


### Update: Correct Wireshark Interface Identified

- Issue: No packets captured initially
- Cause: Incorrect network interface selected
- Fix:
  - Observed which interface showed activity during ping
  - Identified Ethernet 2 as the active interface
  - Used Ethernet 2 for capturing traffic successfully
<img width="779" height="592" alt="07-wireshark-ssh" src="https://github.com/user-attachments/assets/7c11f753-de50-47e8-a4f6-c9ead93bdec7" />

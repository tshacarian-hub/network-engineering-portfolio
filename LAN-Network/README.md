# LAN Network Project (Cisco Packet Tracer)

## Overview
This project demonstrates a basic Local Area Network (LAN) using VLAN segmentation in Cisco Packet Tracer.

## Network Design
- 1 Cisco 2960 Switch
- 4 PCs
- VLAN 10 (IT Department)
- VLAN 20 (HR Department)
<img width="802" height="403" alt="Topology" src="https://github.com/user-attachments/assets/9a706539-24ac-45fd-970a-63d4ec4d2057" />

## IP Addressing
IT VLAN:
- 192.168.10.10
- 192.168.10.11

HR VLAN:
- 192.168.20.10
- 192.168.20.11
<img width="701" height="711" alt="PC IP config" src="https://github.com/user-attachments/assets/0ee71fc7-5588-4d14-91be-4d47a6dfe1b5" />

## Configuration Steps

### VLAN Creation
vlan 10
name IT

vlan 20
name HR
<img width="713" height="725" alt="VLAN creation commands" src="https://github.com/user-attachments/assets/008e4652-47d5-42ab-9880-5b2327200180" />

### Assign Ports
Fa0/1–2 → VLAN 10  
Fa0/3–4 → VLAN 20  
<img width="702" height="715" alt="Port assignment" src="https://github.com/user-attachments/assets/186b8989-ed8d-4014-8ee1-75269b5e36a3" />

## Verification
show vlan brief
<img width="709" height="726" alt="VLAN table output" src="https://github.com/user-attachments/assets/ed99f5d1-3677-4389-9a83-3997d144c784" />

## Testing
- Same VLAN communication: SUCCESS
- Different VLAN communication: FAILED

<img width="1795" height="743" alt="Fail Ping" src="https://github.com/user-attachments/assets/9d916394-32f9-4104-b20d-0f53a0c0d785" />
<img width="1804" height="786" alt="PC0 successful ping to PC1" src="https://github.com/user-attachments/assets/fbdda4dd-0663-4273-b724-cd5a8fd87ebd" />
<img width="1791" height="763" alt="PC2 successful ping to PC3" src="https://github.com/user-attachments/assets/9476ef4a-5a67-479e-bf51-2f5db8ab801f" />

## Key Concepts
- VLAN segmentation improves security
- Switches isolate broadcast domains
- Inter-VLAN communication requires a router

## Tools Used
- Cisco Packet Tracer

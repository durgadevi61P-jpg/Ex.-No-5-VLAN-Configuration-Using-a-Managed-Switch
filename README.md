# Ex. No: 5 VLAN Configuration Using a Managed Switch
# Date: 27/10/2026
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.

# Apparatus/Tools Required
• Cisco Packet Tracer
• 1 Managed Switch (e.g., 2960)
• 4 PCs
• Straight-through Ethernet cables

# Network Topology Diagram
Description:
• PC0 and PC1 are assigned to VLAN 10.
• PC2 and PC3 are assigned to VLAN 20.
• All PCs are connected to different ports on the same switch.

<img width="1535" height="767" alt="Screenshot 2026-10-27 221041" src="https://github.com/user-attachments/assets/55640830-5d2e-4713-9555-8c58608f48cf" />

# IP Addressing Table
Device VLAN IP Address Subnet Mask Port
PC0 10 192.168.10.1 255.255.255.0 FastEthernet0/1
PC1 10 192.168.10.2 255.255.255.0 FastEthernet0/2
PC2 20 192.168.20.1 255.255.255.0 FastEthernet0/3
PC3 20 192.168.20.2 255.255.255.0 FastEthernet0/4

# Procedure
Open Cisco Packet Tracer and add 4 PCs and 1 Switch.
Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.
Assign static IP addresses to each PC as per the IP table.
Enter the Switch CLI and create two VLANs:
o VLAN 10 for PC0 and PC1
o VLAN 20 for PC2 and PC3
Assign the respective switch ports to their VLANs.
Use the ping command from PC0 to PC1 (should succeed).
Try pinging from PC0 to PC2 (should fail — different VLANs).
Commands Used (Switch CLI)
bash
CopyEdit
Switch> enable
Switch# configure terminal

Switch(config)# vlan 10
Switch(config-vlan)# name STAFF
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name STUDENTS
Switch(config-vlan)# exit

Switch(config)# interface range fastethernet0/1 - 2
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 10
Switch(config-if-range)# exit

Switch(config)# interface range fastethernet0/3 - 4
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit

# Output 
<img width="1535" height="756" alt="Screenshot 2026-10-27 221705" src="https://github.com/user-attachments/assets/9c37c433-073a-4155-a26b-1be60bd061ca" />
<img width="1533" height="760" alt="Screenshot 2026-10-27 222314" src="https://github.com/user-attachments/assets/899ac06a-2d44-4404-ba59-2f7f32f70e53" />


# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

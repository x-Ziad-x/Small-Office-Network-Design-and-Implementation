# Small Office Network Design and Implementation

## Project Overview

This project demonstrates the design and implementation of a secure, segmented network for a small office environment with multiple departments (Management, Technical, Sales, Financial, and Secretary). The solution uses VLANs for network segmentation, inter-VLAN routing for communication between departments, and implements security features like SSH access and access control lists.

## Key Features

- **VLAN Segmentation**: Logical separation of department networks
- **Inter-VLAN Routing**: Secure communication between departments
- **SSH Access**: Encrypted remote management
- **Port Security**: Protection against unauthorized access
- **DHCP Services**: Automatic IP address assignment
- **Access Control**: Restricted management access

## Project Files

- `Configuration.docx`: Contains complete switch configurations
- `DEPI Graduation Project Report.pdf`: Full project documentation
- `Small_Office_Network.pkt`: Cisco Packet Tracer simulation file
- `README.md`: This file

## Network Configuration Highlights

### VLAN Assignments

| VLAN ID | Department    | Network Address    |
|---------|---------------|--------------------|
| 1       | Technical     | 192.168.1.0/24     |
| 10      | Management    | 192.168.10.0/24    |
| 20      | Secretary     | 192.168.20.0/24    |
| 30      | Sales         | 192.168.30.0/24    |
| 40      | Financial     | 192.168.40.0/24    |

### Switch Configuration Examples

```cisco
! Switch 0 (Technical)
hostname technical
interface FastEthernet0/1
 switchport mode trunk
interface Vlan1
 ip address 192.168.1.100 255.255.255.0
ip default-gateway 192.168.1.1

! Switch 1 (Sales/Financial)
hostname finSales
interface FastEthernet0/2
 switchport access vlan 30
 switchport mode access
interface Vlan30
 ip address 192.168.30.100 255.255.255.0

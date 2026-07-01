# DHCP-Implementation-Using-GNS3
Implemented and simulated DHCP services using GNS3, automated IP address allocation, analyzed DHCP DORA packet exchange using Wireshark, and verified network connectivity through end-to-end testing.

# DHCP Implementation using GNS3 Tool

## Project Overview

This project demonstrates the implementation and simulation of the Dynamic Host Configuration Protocol (DHCP) using the GNS3 network simulation platform. The project focuses on automating IP address allocation to network devices, analyzing the DHCP packet exchange process using Wireshark, and verifying network connectivity between clients and routers.

The network consists of a DHCP Server Router, DHCP Client Router, and end-user PCs connected through a Layer-2 switch.

---

## Objectives

- Configure and implement DHCP services using Cisco IOS routers.
- Automate IP address assignment for network devices.
- Analyze DHCP packet exchanges using Wireshark.
- Verify network connectivity using ICMP ping.
- Understand DHCP server and client operations.
- Demonstrate efficient IP address management.

---

## Technologies Used

- GNS3
- Cisco IOS Routers
- DHCP
- VPCS
- Ethernet Switch
- Wireshark
- ICMP
- Solar-PuTTY

---

## Network Topology

Topology image is available in:

topology/DHCP_Network_Topology.png

---

## Network Architecture

The network consists of:

- R1 configured as the DHCP Server.
- R2 configured as a DHCP Client.
- PC1 configured as a DHCP Client.
- PC2 configured as a DHCP Client.
- Switch1 providing Layer-2 connectivity.

---

## IP Addressing

### DHCP Pool Configuration

| Parameter | Value |
|-----------|--------|
| Network | 192.168.1.0/24 |
| Default Gateway | 192.168.1.100 |
| DNS Server 1 | 192.168.1.101 |
| DNS Server 2 | 192.168.1.102 |

---

### Device Addressing

| Device | Interface | IP Address |
|---------|----------|------------|
| R1 (DHCP Server) | e6/0 | 192.168.1.100 |
| R2 | e6/0 | DHCP Assigned (192.168.1.2) |
| PC1 | e0 | DHCP Assigned (192.168.1.1) |
| PC2 | e0 | DHCP Assigned (192.168.1.3) |

---

## DHCP Server Configuration

### Router: R1

Configured R1 as the DHCP server using the following DHCP pool:

```bash
ip dhcp pool SBI-BANK
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.100
 dns-server 192.168.1.101 192.168.1.102

### Verification Commands

#### DHCP Server Verification (R1)

Verification performed using:

```bash
show running-config | section dhcp
show ip dhcp binding
show ip dhcp pool
```

---

### DHCP Client Configuration

#### Router: R2

Configured R2 interface to obtain IP address automatically:

```bash
interface e6/0
 ip address dhcp
 no shutdown
```

Verification performed using:

```bash
show ip interface brief
show dhcp lease
```

---

### DHCP DORA Process Analysis

The DHCP packet exchange process was analyzed using Wireshark.

#### DHCP Packet Sequence

- DHCP Discover
- DHCP Offer
- DHCP Request
- DHCP Acknowledgement

This process confirms successful IP address allocation from the DHCP server to network clients.

---

### Verification

#### PC1 Verification

PC1 successfully obtained an IP address using:

```bash
ip dhcp
```

Assigned:

```text
IP Address : 192.168.1.1/24
Gateway    : 192.168.1.100
```

---

#### Router R2 Verification

Verified DHCP address assignment using:

```bash
show ip interface brief
```

Assigned:

```text
Ethernet6/0 : 192.168.1.2
```

---

#### PC2 Verification

PC2 successfully obtained an IP address using:

```bash
ip dhcp
```

Assigned:

```text
IP Address : 192.168.1.3/24
Gateway    : 192.168.1.100
```

---

### Connectivity Test

#### PC1 to PC2

```bash
ping 192.168.1.3
```

Successful communication verified.

#### PC2 to R1

```bash
ping 192.168.1.100
```

Successful communication verified.

#### R2 to R1

```bash
ping 192.168.1.100
```

Successful communication verified.

---

### DHCP Packet Analysis

Wireshark was used to capture and analyze:

- DHCP Discover packets
- DHCP Offer packets
- DHCP Request packets
- DHCP Acknowledgement packets
- ARP packets
- ICMP packets

---

### Screenshots

Available in the screenshots folder:

- 01_GNS3_Topology_With_Wireshark.png
- 02_PC1_DHCP_Verification.png
- 03_Router_R2_DHCP_Verification.png
- 04_PC2_DHCP_Verification.png
- 05_DHCP_Server_Configuration.png

---

### Project Structure

DHCP-Implementation-Using-GNS3

├── README.md

├── topology

│   └── DHCP_Network_Topology.png

├── screenshots

│   ├── 01_GNS3_Topology_With_Wireshark.png

│   ├── 02_PC1_DHCP_Verification.png

│   ├── 03_Router_R2_DHCP_Verification.png

│   ├── 04_PC2_DHCP_Verification.png

│   └── 05_DHCP_Server_Configuration.png

├── configurations

│   ├── PC1_DHCP_Client_Configuration.txt

│   ├── PC2_DHCP_Client_Configuration.txt

│   ├── R1_Router_DHCP_Server_Configuration.txt

│   └── R2_Router_DHCP_Client_Configuration.txt

└── project file

    └── DHCP_Implementation_Lab.gns3

---

### Learning Outcomes

- DHCP Configuration
- DHCP Server Implementation
- DHCP Client Configuration
- DHCP DORA Packet Analysis
- Wireshark Packet Capturing
- Network Troubleshooting
- IP Address Management
- Cisco Router Configuration
- Network Verification
- GNS3 Network Simulation

---

### Author

Chanakya Burugu

Computer Science and Engineering (Networks)

Networking and Infrastructure Enthusiast



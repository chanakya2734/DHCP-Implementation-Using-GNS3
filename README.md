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


# Phase 01 – Environment Setup

## Objective

The objective of this phase is to build a controlled lab environment where network traffic can be monitored and controlled through a firewall.

---

## Lab Architecture

The lab environment is composed of two virtual machines connected through a virtual network:

- Firewall: pfSense
- Victim: Ubuntu Server

The firewall acts as a gateway between networks and will be used to monitor and control traffic.

---

## Network Configuration

The environment is configured using VMware virtual networks:

- WAN (VMnet8 - NAT)
  - Used to simulate external network access
- LAN (VMnet1 - Host-Only)
  - Internal network where the Ubuntu server is located

---

## pfSense Setup

The pfSense firewall was installed and configured with two network interfaces:

- WAN Interface (em0)
  - Configured via DHCP
- LAN Interface (em1)
  - IP Address: 192.168.10.1/24
  - DHCP Server: Enabled

The LAN interface provides IP addresses to internal machines.

---

## Ubuntu Setup

The Ubuntu Server machine was configured with:

- Network Adapter: Host-Only (VMnet1)
- IP Address: Assigned automatically via DHCP from pfSense

---

## Connectivity Verification

The connectivity between the firewall and the Ubuntu server was verified using:

- ICMP (ping) tests
- Access to the pfSense web interface from Ubuntu

Successful communication confirms that the lab environment is correctly configured.

---

## Evidence

![pfSense Dashboard](../screenshots/pfsense-dashboard.jpg)

---

## Conclusion

The environment has been successfully set up.

The firewall is operational, and internal network communication is working as expected.  
This provides a solid foundation for configuring firewall rules and simulating security incidents in the next phases.

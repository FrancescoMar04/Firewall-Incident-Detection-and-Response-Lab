# Final Report

## Overview

This project simulates a network environment protected by a pfSense firewall and targeted by an external attacker using Kali Linux.

The objective of the lab was to demonstrate how firewall rules are configured, how network traffic is monitored, and how suspicious activity can be detected and mitigated at the network level.

---

## Lab Summary

The environment consisted of:

- A pfSense firewall used to monitor and filter network traffic  
- An internal Ubuntu server acting as the protected target  
- An attacker machine (Kali Linux) used to simulate malicious activity  

All traffic between the networks was controlled and logged by the firewall.

---

## Incident Summary

During the simulation, multiple suspicious connection attempts were observed in the firewall logs.

Key observations include:

- Repeated connection attempts originating from a single source IP address  
- Traffic targeting multiple destination ports  
- A high number of blocked connections generated in a short period of time  

These activities were generated using network scanning techniques (Nmap) and are consistent with a **port scanning attack**.

---

## Key Findings

- The firewall successfully detected and logged suspicious network activity in real time  
- The majority of incoming connections were blocked according to the default-deny policy  
- Only explicitly allowed services (such as SSH) were reachable  
- The observed traffic pattern clearly indicated reconnaissance behavior  

---

## Lessons Learned

- Continuous monitoring of firewall logs is essential for detecting early-stage attacks  
- A properly configured firewall significantly reduces the attack surface  
- Port scanning activity can be identified through recognizable traffic patterns  
- Log analysis is a critical skill for detecting and understanding potential threats  

---

## Conclusion

This project demonstrates a complete workflow for detecting and responding to network-based threats using a firewall.

It highlights the importance of:

- Proper firewall configuration  
- Traffic monitoring and log analysis  
- Identifying suspicious patterns  
- Applying effective mitigation strategies  

Overall, the lab provided practical experience in network security and improved understanding of how real-world attacks can be detected and handled at the firewall level.

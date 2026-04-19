# Firewall Incident Detection and Response Lab

## Overview

This project simulates a security incident in a controlled lab environment using a firewall-based approach.

The objective is to demonstrate how network traffic can be controlled, monitored, and analyzed, followed by a structured incident response process.

---

## Simulated Incident

The lab simulates a network-based security incident involving unauthorized access attempts and suspicious traffic patterns.

These activities are monitored and controlled through firewall rules, allowing detection and response at the network level.

---

## Workflow

1. Environment setup  
2. Firewall installation and configuration  
3. Rule creation and traffic control  
4. Attack simulation  
5. Detection, analysis, and response  
6. Final report  

---

## Lab Architecture

The firewall is positioned between the attacker and the victim to monitor and control network traffic.

* **Firewall:** pfSense  
* **Victim:** Ubuntu Server  
* **Attacker:** Kali Linux  

---

### Network Configuration

* NAT (internet access)  
* Internal network for communication between machines  
* Firewall positioned as a gateway between attacker and victim  

---

## What You Will Find in `phases/`

* Step-by-step firewall configuration  
* Network traffic analysis  
* Attack simulation and detection  
* Incident investigation and response  
* Final report with findings  

---

## Key Skills Demonstrated

* Firewall rule configuration and traffic filtering  
* Network traffic monitoring and analysis  
* Detection of unauthorized access attempts  
* Incident response based on network-level events  

---

## Tools Used

* pfSense (firewall platform)  
* Ubuntu Server (target system)  
* Kali Linux (attack simulation)  

---

## Project Outcome

This project demonstrates how firewalls can be used to monitor, control, and analyze network traffic to detect and respond to potential security incidents.

It highlights the role of network-level defenses in identifying and mitigating unauthorized access attempts.

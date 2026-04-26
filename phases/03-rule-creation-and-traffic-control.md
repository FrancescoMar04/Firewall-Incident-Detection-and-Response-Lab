# Phase 03 – Rule Creation and Traffic Control

## Objective

The objective of this phase is to implement controlled firewall rules in order to allow specific traffic while maintaining a secure default-deny posture.

---

## Context

In Phase 02, the firewall was configured with a strict default-deny policy on the WAN interface, blocking all incoming connections from external networks.

This phase introduces a controlled exception to simulate a real-world scenario where a specific service must be accessible while minimizing the attack surface.

---

## Scenario

An SSH service is deployed on the internal Ubuntu server.

The goal is to allow access to this service **only from the attacker network (OPT1)** while ensuring that all other traffic remains blocked.

---

## Service Preparation

The SSH service was installed and verified on the Ubuntu server:

- OpenSSH Server installed
- Service running on port 22

Before applying any firewall rule:

- All connection attempts from the attacker network were blocked
- TCP connections resulted in timeouts

---

## Firewall Rule Implementation

A firewall rule was created on the OPT1 interface of pfSense.

### Rule Configuration

- Interface: OPT1 (Attacker Network)
- Protocol: TCP
- Source: any
- Destination: Ubuntu Server (192.168.10.128)
- Destination Port: 22 (SSH)

This rule allows SSH traffic from the attacker network to the internal server.

---

## Traffic Control Validation

After applying the rule, connectivity tests were performed from the attacker machine (Kali Linux).

### Allowed Traffic

nc -zv 192.168.10.128 22

Result:

- Connection successful
- SSH service reachable

---

### Blocked Traffic

nc -zv 192.168.10.128 80

Result:

- Connection timed out

---

## Security Considerations

This configuration follows the principle of **least privilege**:

- Only the required service (SSH) is exposed
- Access is limited to a specific network segment
- All other traffic remains blocked

---

## Real-World Note

In a real-world scenario, external access typically originates from the WAN interface.

In such cases, exposing an internal service would require:

- NAT (port forwarding)
- A corresponding firewall rule on the WAN interface

In this lab, the OPT1 interface is used to simulate an attacker network without exposing services to the actual internet.

---

## Evidence

### Firewall Rule (OPT1)

![OPT1 Rule](../screenshots/opt1-rule-ssh.jpg)

### Successful SSH Connectivity Test

![SSH Test](../screenshots/ssh-success.jpg)

---

## Conclusion

A controlled firewall rule was successfully implemented to allow SSH access from a specific network segment.

The firewall maintains a secure posture by:

- Allowing only explicitly defined traffic
- Blocking all other connections
- Preserving network segmentation

This phase demonstrates effective traffic control and prepares the environment for attack simulation.

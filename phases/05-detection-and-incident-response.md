# Phase 05 – Detection and Incident Response

## Objective

The objective of this phase is to analyze firewall logs in order to identify suspicious activity, detect potential threats, and apply appropriate mitigation measures.

This phase focuses on transforming raw network data into actionable security decisions.

---

## Detection Approach

Traffic generated during the attack simulation phase was analyzed using the firewall logging capabilities of pfSense.

The analysis focused on identifying patterns that indicate malicious or suspicious behavior.

---

## Log Analysis (Live Firewall Logs)

Firewall logs were reviewed to observe real-time traffic patterns.

### Key Observations

- Multiple connection attempts originating from a single source IP: **192.168.20.129**
- Traffic targeting multiple destination ports on the internal server (**192.168.10.128**)
- A high number of blocked connections across different ports
- Limited successful connections corresponding only to explicitly allowed services (SSH)

This behavior is consistent with a **port scanning activity**, where an attacker probes multiple ports to discover exposed services.

---

## Evidence – Scan Pattern

![Firewall Scan Pattern](../screenshots/firewall-scan-pattern.jpg)

---

## Statistical Analysis

To further validate the observed behavior, aggregated firewall log data was analyzed.

### Key Findings

- **100% of traffic originated from a single source IP**, indicating a focused attack
- A high volume of connection attempts (~10,000 events) in a short time frame
- The vast majority of traffic was blocked by the firewall
- Only a minimal number of connections were allowed (SSH), consistent with configured rules
- Traffic distribution across multiple destination ports confirmed reconnaissance activity

This statistical perspective reinforces the identification of a scanning pattern.

---

## Evidence – Statistical Overview

![Firewall Statistical Analysis](../screenshots/firewall-statistical-analysis.jpg)

---

## Threat Identification

Based on the analysis of both raw firewall logs and aggregated statistical data, the observed activity was classified as:

Port Scanning / Reconnaissance Activity

### Indicators

- Repeated connection attempts from a single source IP address
- Sequential probing of multiple destination ports
- High volume of traffic generated in a short period of time
- Predominantly blocked connections with limited allowed traffic

These characteristics are consistent with reconnaissance behavior, where an attacker attempts to identify exposed services and potential entry points within a target system.

---

## Incident Response

Following the identification of suspicious activity, a mitigation strategy was implemented to prevent further interaction from the attacker.

### Action Taken

A firewall rule was created to block all traffic originating from the identified source IP:

- Source: 192.168.20.129  
- Destination: any  
- Protocol: any  
- Action: Block  

The rule was placed at the top of the rule set to ensure it takes precedence over existing rules.

---

## Evidence – Block Rule

![Block Rule](../screenshots/opt1-block-attacker-rule.jpg)

---

## Verification

To validate the effectiveness of the implemented mitigation:

1. The scanning activity was repeated from the attacker machine
2. All connection attempts were denied by the firewall
3. No services on the target system were reachable

This confirms that the firewall rule successfully prevented further reconnaissance attempts.

---

## Evidence – Post-Block Scan

![Nmap After Block](../screenshots/nmap-after-block.jpg)

---

## Evidence – Blocked Traffic Logs

![Blocked Traffic](../screenshots/firewall-blocked-traffic.jpg)

---

## Final Outcome

- The suspicious activity was successfully detected through firewall log analysis
- The attacker was clearly identified and isolated
- The firewall effectively enforced the mitigation rule
- Further interaction between the attacker and the internal network was prevented

---

## Conclusion

This phase demonstrates a complete detection and incident response workflow:

- Identification of anomalous network behavior  
- Correlation between raw logs and statistical analysis  
- Classification of the threat  
- Implementation of a targeted mitigation strategy  
- Verification of the effectiveness of the response  

This approach reflects a real-world security operations process, where network-level visibility is leveraged to detect and respond to potential threats in a structured and effective manner.

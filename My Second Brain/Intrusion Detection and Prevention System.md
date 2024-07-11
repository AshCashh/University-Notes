---
alias: IDS/IPS
tags: [networks]
Created: 2023-09-16T18:30:02+10:00
Modified: 2024-07-03T19:35:33+10:00
---
# Intrusion Detection System
An intrusion detection system (IDS) monitors network traffic for malicious packets or traffic patterns and reports identified security breaches to a management station. An IDS can be either a host-based or network-based system but typically passive.
# Intrusion Prevention System
An intrusion prevention system (IPS) is a active system that can take countermeasures if an attack is in progress. It does so via:
- [[Firewall]] reconfiguration
- Connection termination / reset
- Disabling the link between external/internal N/Ws
# Security Solutions
Preventative:
- To block unauthorised network activity from occurring, e.g. antivirus, firewalls, IPSs
Detection: 
- To detect unauthorised activity in progress or after it has occurred, e.g. honeypots, IDSs
Corrective:
- To repair damage or restore resources, e.g. patching a vulnerable system, quarantining a virus.
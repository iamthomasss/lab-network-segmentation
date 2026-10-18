# lab-network-segmentation
Segmented home lab: OPNsense firewall separating victim and attacker zones, with default-deny rules and logging. 

## Goal
A segmented home lab with OPNsense separating a victim zone from an attacker zone, so every attack crosses a firewall that controls and logs it.

## Job skills shown
- Network security and segmentation
- Firewalls (rule design, default deny, logging)
- Security infrastructure implementation and maintenance

## Network diagram
![Lab network diagram](lab-network-diagram.png)

## IP plan
(paste your table)

## Intended firewall rules
1. Win10 and Ubuntu may reach the internet on web ports on HTTP (80) and HTTPS (443), and OPNsense on DNS (53), so they can browse and get updates
2. Kali may reach the internet on web ports HTTP (80) and HTTPS (443), and OPNsense on DNS (53) so they can browse and get updates.
3. Kali may reach Ubuntu on SSH (22), and Win10 on SMB (445) and RDP (3389) to practice common attacks. Logged.
4. Win10 and Ubuntu may start connections to Kali only on Port 4444 (for simplicity), logged, so phone-home attacks work and are recorded. Although real attackers tend to hide on 443.
5. Only Win10 may reach OPNsense's admin page (HTTPS 443). Keeping it reachable from as few places as possible. Kali should never be able to access it.
6. Default deny with logging.
7. No Lab machine may reach my home network (192.168.0.x) or the T14 (192.168.230.1). Logged.

** Rule 7 must sit above rules 1 and 2. Rule 6 is always last. 



## Known trade-offs
- The firewall is managed from Win10, a "victim" machine. In production this would be a separate management zone.
- Phone-home port 4444 is used for simplicity. Real attackers often use 443 to blend in.

## Status
Week 0: design complete. Build starts 19 Oct 2026.

[Day02_VLAN_Lab.md](https://github.com/user-attachments/files/34042980/Day02_VLAN_Lab.md)
# Day 02 – VLAN Segmentation & Access Control

## 1. Project Objective

Logically separate four departments in a company network using VLANs, configure inter-VLAN routing, and restrict access from the guest network.

## 2. Equipment Used

- Cisco Packet Tracer
- 1 × Cisco 2911 router
- 1 × Cisco 2960 switch
- 7 × PCs

## 3. Network Configuration

| VLAN | Department | Network | Gateway |
|---|---|---|---|
| 10 | HR | 192.168.10.0/24 | 192.168.10.1 |
| 20 | IT | 192.168.20.0/24 | 192.168.20.1 |
| 30 | GUEST | 192.168.30.0/24 | 192.168.30.1 |
| 40 | MANAGEMENT | 192.168.40.0/24 | 192.168.40.1 |

An 802.1Q trunk connects the switch and the router. Router subinterfaces provide inter-VLAN routing.

## 4. Security Configuration

An extended ACL named `GUEST_FILTER` restricts IP traffic from the guest network to internal networks.

Blocked destination networks:
- HR – 192.168.10.0/24
- IT – 192.168.20.0/24
- MANAGEMENT – 192.168.40.0/24

The ACL is applied inbound on the router's `G0/0.30` subinterface.

This ACL is not a substitute for a full stateful firewall.

## 5. Troubleshooting

**Issue 1: The trunk connection did not appear during verification.**

Cause: The router's physical interface was administratively shut down.

Solution: Enabled the interface using the `no shutdown` command.

**Issue 2: The ACL did not block access to the MANAGEMENT network.**

Cause: The new `deny` rule was placed after a `permit` rule.

Solution: Used ACL sequence numbers to position the deny rule before the permit rule.

## 6. Connectivity Tests

- GUEST → HR: blocked
- GUEST → IT: blocked
- GUEST → MANAGEMENT: blocked
- GUEST → GUEST: successful
- HR → IT: successful
- MANAGEMENT → HR: successful
- MANAGEMENT → IT: successful

## 7. Result

Based on the planned tests, the VLANs, trunk connection, router subinterfaces, and ACL worked as intended.

During this lab, I practiced network segmentation, inter-VLAN routing, ACL rule ordering, and network troubleshooting.

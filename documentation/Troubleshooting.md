
# Troubleshooting Overview

This document records issues encountered during the deployment of the homelab and the troubleshooting process used to identify and resolve them.

---

# Issue 1 - OPNsense Interface Mapping

## Problem

Internet access became unreachable because the WAN and LAN network interfaces were assigned to the wrong virtual network adapters within the OPNsense virtual machine.

---

## Symptoms

- Unable to access the OPNsense web interface.
- No Internet connectivity from internal virtual machines.
- Traffic appeared to stop at the firewall.
- Pings to external hosts failed.

---

## Troubleshooting

- Verified connectivity by pinging devices from both the LAN and WAN interfaces.
- Reviewed firewall rules to ensure traffic was not being blocked.
- Verified Source NAT configuration.
- Confirmed all IP addressing and subnet configurations were correct.
- Inspected physical network topology and bridge assignments.
- Compared OPNsense interface assignments with the Proxmox virtual bridge (vmbr) mappings.
- Confirmed the virtual NIC order matched the intended network design.

---

## Root Cause

The OPNsense WAN and LAN interfaces were connected to the wrong Proxmox virtual bridges. As a result, traffic was entering and leaving the incorrect networks, preventing proper routing and firewall access.

---

## Solution

Reassigned the OPNsense virtual network adapters to the correct Proxmox bridges.

| Interface | Correct Bridge |
|-----------|----------------|
| WAN | vmbr0 |
| LAN (VLAN Trunk) | vmbr2 |

After correcting the interface assignments, Internet connectivity and access to the OPNsense web interface were restored.

---

# Issue 2 - Missing Source NAT Rules

## Problem

Virtual machines on the backend VLAN could communicate with OPNsense but were unable to access the Internet.

---

## Symptoms

- Internal devices could ping the OPNsense gateway.
- OPNsense could successfully reach Internet hosts.
- Virtual machines could not reach external IP addresses.
- DNS resolution occasionally worked, but Internet traffic failed.

---

## Troubleshooting

- Verified VLAN firewall rules allowed outbound traffic.
- Confirmed default gateways were configured correctly.
- Verified DNS configuration.
- Tested connectivity using ICMP and traceroute.
- Reviewed outbound NAT configuration.
- Checked Automatic Outbound NAT rule generation.

---

## Root Cause

Automatic Outbound NAT failed to generate translation rules for the VLAN networks. Without Source NAT, private IP addresses could not be translated to the WAN interface, preventing Internet access.

---

## Solution

Changed the outbound NAT mode from **Automatic** to **Hybrid** and manually created Source NAT rules for each VLAN.

| Source Network | Translation |
|---------------|-------------|
| 192.168.10.0/24 | WAN Interface Address |
| 192.168.20.0/24 | WAN Interface Address |

Once the rules were applied, Internet connectivity was restored for all VLANs.

---

# Issue 3 - 

## Problem

x

---

## Symptoms

- x
- x
- x.
- x

---

## Troubleshooting

- x
- x
- x
- x
- x
- x
- x

---

## Root Cause

x
---

## Solution

x
---

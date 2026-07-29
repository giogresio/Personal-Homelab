# Network Design

The homelab network is designed to simulate a small enterprise environment using network segmentation, centralized routing, and virtualized infrastructure. OPNsense serves as the core firewall and router, providing inter-VLAN routing, NAT, DHCP, and firewall services.

Network segmentation isolates infrastructure services from client devices while allowing controlled communication through firewall rules.

---

# Network Design

```text
                    Internet
                        │
                 Router/Modem/AP
                        │
                  vmbr0 (WAN)
                        │
                 OPNsense Firewall
                        │
                 vmbr2 (LAN Trunk)
              ┌─────────┴─────────┐
              │                   │
          VLAN 10             VLAN 20
      Infrastructure          Clients
```

---


# VLAN Design

## VLAN 10 – Infrastructure

Hosts all critical infrastructure services.

### Devices

- Windows Server
- TrueNAS SCALE
- Ubuntu Server
- Future infrastructure services

### Purpose

- Active Directory
- DNS
- SMB Storage
- Docker Services
- Internal administration

---

## VLAN 20 – Client Network

Hosts workstation and end-user devices.

### Purpose

- Client access
- Internet browsing
- Controlled access to backend resources

---

# Firewall Strategy

Firewall policies follow the principle of least privilege.

### Backend VLAN

- DNS
- Full outbound Internet access
- SMB file access
- Administrative access to infrastructure
- Communication between backend services

### Client VLAN

- Internet access
- DNS (Windows Server)
- DHCP (OPNsense)
- Active Directory authentication
- SMB file access (TrueNAS)
- Restricted access to backend systems

---

# Virtual Networking

The virtual network is built using Proxmox Linux Bridges.

| Bridge | Function |
|---------|----------|
| vmbr0 | WAN Connection |
| vmbr1 | Proxmox Management |
| vmbr2 | VLAN Trunk |

OPNsense connects directly to the WAN bridge and provides routing for all internal VLANs through the VLAN-aware LAN bridge.

---

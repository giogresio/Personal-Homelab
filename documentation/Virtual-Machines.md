# Virtual Machines

The homelab consists of four virtual machines running on Proxmox VE. Each VM provides a dedicated services commonly found in enterprise environments.

---

# Virtual Machine Summary

| VM Name | Operating System | vCPUs | RAM | Storage | IP Address | Primary Role |
|---------|------------------|:-----:|----:|--------:|------------|--------------|
| OPNsense | OPNsense | 2 | 4 GB | 100 GB | WAN: 192.168.50.100<br>VLAN10: 192.168.10.2<br>VLAN20: 192.168.20.2 | Firewall, Routing, NAT, VLANs, DHCP |
| WindowsAD | Windows Server 2022 | 3 | 4 GB | 100 GB | 192.168.10.30 | Active Directory & DNS |
| TrueNAS | TrueNAS SCALE | 2 | 8 GB | 100 GB + 1 TB SATA SSD | 192.168.10.20 | SMB File Server |
| Ubuntu | Ubuntu Server LTS | 6 | 12 GB | 200 GB | 192.168.10.40 | Docker Host |

---

# OPNsense Firewall

## Purpose

Serves as the central router and firewall for the homelab by managing network traffic between VLANs and providing secure Internet access.

---

# Windows Server 2022

## Purpose

Provides centralized identity management and name resolution for devices on the backend network.

---

# TrueNAS SCALE

## Purpose

Provides centralized network storage for virtual machines and client systems.

---

# Ubuntu Server

## Purpose

Hosts Docker containers and Linux-based services for the homelab.


# VM Relationships

OPNsense - offers routing and segmentation for the rest of the VMs 

Windows Server - offers DNS services for the other servers

TrueNAS - offers File storage services for the other servers 

```


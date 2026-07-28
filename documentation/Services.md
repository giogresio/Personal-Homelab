# Services

This homelab provides several core infrastructure services commonly found in enterprise environments. Services are distributed across virtual machines to improve both scalability as well as to maintain the space and noise within my room as I keep the server rack next to my desk setup to have access to the audio equipment within the rack.

---

# Infrastructure Services

| Service | Host | Purpose | Protocol(s) | Port(s) |
|----------|------|---------|-------------|---------|
| Firewall | OPNsense | Filters and secures network traffic | TCP/UDP | ALL |
| Routing | OPNsense | Routes traffic between VLANs and the Internet | IP | N/A |
| Network Address Translation (NAT) | OPNsense | Translates private IP addresses for Internet access | IP | N/A |
| DHCP | OPNsense | Assigns IP addresses to client devices | UDP | 67, 68 |
| Active Directory Domain Services | Windows Server 2022 | User authentication and domain management | TCP/UDP | 88, 389, 636 |
| DNS | Windows Server 2022 | Internal name resolution | TCP/UDP | 53 |
| SMB File Sharing | TrueNAS SCALE | Shared network storage | TCP | 445 |
| Docker Engine | Ubuntu Server | Container virtualization platform | TCP | 2375/2376* |
| Portainer | Ubuntu Server | Docker web management interface | TCP | 9443 |


---

# OPNsense Services

## Firewall

Provides stateful packet inspection and controls all traffic entering and leaving the network.

### Features

- Stateful packet filtering
- VLAN firewall policies
- Access control
- Traffic inspection

---

## Routing

Routes traffic between VLANs and external networks.

### Responsibilities

- Inter-VLAN routing
- Default gateway
- Internet access
- Network segmentation

---

## Network Address Translation (NAT)

Allows private IP addresses to communicate with public Internet resources.

### Configuration

- Outbound Source NAT
- Hybrid NAT Mode
- VLAN 10 Translation
- VLAN 20 Translation

---

## DHCP

Automatically assigns IP addresses to client devices.

### Functions

- IP address allocation
- Gateway assignment
- DNS assignment
- Lease management

---

# Windows Server Services

## Active Directory Domain Services (AD DS)

Provides centralized authentication and directory services.

### Responsibilities

- User authentication
- Computer authentication
- Domain management
- Security policy enforcement

---

## Domain Name System (DNS)

Resolves hostnames to IP addresses within the internal network.

### Responsibilities

- Internal DNS resolution
- Domain records
- Forward lookups
- Reverse lookups

---

# TrueNAS SCALE Services

## SMB File Sharing

Provides centralized storage accessible by authorized users and systems.

### Responsibilities

- Shared folders
- User permissions
- Network file storage
- Backup repository

---

# Ubuntu Server Services

## Docker Engine

Runs containerized applications in isolated environments.

### Responsibilities

- Container deployment
- Image management
- Resource isolation

---

## Portainer

Provides a graphical interface for managing Docker containers.

### Responsibilities

- Container management
- Image management
- Volume management
- Network management

---


# Service Architecture

```text
                    Internet
                        │
                 Home Router
                        │
                 OPNsense Firewall
            Firewall │ Routing │ NAT │ DHCP
                        │
          ┌─────────────┴─────────────┐
          │                           │
     Infrastructure VLAN         Client VLAN
          │
    ┌─────┼──────────────┐
    │     │              │
Windows  TrueNAS      Ubuntu
Server    SCALE        Server
  │         │             │
AD/DNS    SMB NAS      Docker
                          │
                     Portainer
```

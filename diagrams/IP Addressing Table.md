
## IP Address Table

| Device | Interface | IP Address | Subnet | Gateway | VLAN | Purpose |
|---------|-----------|------------|--------|---------|------|---------|
| Home Router | Switch (Ethernet) | 192.168.50.1 | /24 | (private) | NA | Internet Gateway |
| Proxmox VE | Vmbr1 | 192.168.50.50 | /24 | 192.168.50.1 | NA | Hypervisor Management |
| OPNsense | Vmbr0 | 192.168.50.100 | /24 | 192.168.50.1 | NA | Firewall/DHCP/Home Network Access |
| OPNsense | Vmbr2 | 192.168.10.2 | /24 | (Itself) | 10 | Backend Gateway |
| OPNsense | Vmbr2 | 192.168.20.2 | /24 | (Itself) | 20 | Frontend Gateway |
| Windows Server 2022 | Vmbr2 | 192.168.10.30 | /24 | 192.168.10.2 | 10 | Active Directory/DNS |
| TrueNAS SCALE | Vmbr2 | 192.168.10.20 | /24 | 192.168.10.2 | 10 | Network File Storage |
| Ubuntu Server | Vmbr2 | 192.168.10.40 | /24 | 192.168.10.2 | 10 | Docker Host |
| Portainer | Vmbr2 | 192.168.10.41 | /24 | 192.168.10.2 | 10 | Docker Management |
| Client PC (Wireless) | Wifi AP | 192.168.50.10 | /24 | 192.168.50.1 | NA | WAN Access Desktop Interface |
| Client PC (Ethernet) | Ethernet | 192.168.10.10 | /24 | 192.168.10.2 | 10 | VLAN Access Desktop Interface |

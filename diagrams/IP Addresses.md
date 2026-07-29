
## IP Address Table

| Device | Interface | IP Address | Subnet | Gateway | VLAN | Purpose |
|---------|-----------|------------|--------|---------|------|---------|
| Home Router | Ethernet | 192.168.50.1 | /24 | (private) | NA | Internet Gateway |
| Proxmox VE | Vmbr1 | 192.168.50.50 | /24 | 192.168.50.1 | NA | Hypervisor Management |
| OPNsense | Vmbr0 | 192.168.50.100 | /24 | 192.168.50.1 | NA | Firewall/DHCP/Home Network Access |
| OPNsense | Vmbr2 | 192.168.10.2 | /24 |  192.168.50.100 | 10 | Backend Gateway |
| OPNsense | Vmbr2 | 192.168.20.2 | /24 |  192.168.50.100 | 20 | Frontend Gateway |
| Windows Server 2022 | Vmbr2 | 192.168.10.30 | /24 | 192.168.10.2 | 10 | Active Directory/DNS |
| TrueNAS SCALE | Vmbr2 | 192.168.10.20 | /24 | 192.168.10.2 | 10 | Network File Storage |
| Ubuntu Server | Vmbr2 | 192.168.10.40 | /24 | 192.168.10.2 | 10 | Docker Host |
| Portainer | Vmbr2 | 192.168.10.41 | /24 | 192.168.10.2 | 10 | Docker Management |
| GUI Access PC | Ethernet | 192.168.50.10 | /24 | 192.168.50.1 | NA | WAN Access Desktop Interface |

## Static Routes

| Device | Destination | Gateway | Purpose |
|--------|-------------|---------|---------|
| Home Router | 192.168.10.0/24 | 192.168.50.100 | GUI Access PC to Backend VLAN |

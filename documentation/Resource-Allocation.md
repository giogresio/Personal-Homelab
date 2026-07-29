# Resource Allocation

## Hypervisor Hardware Specifications

| Component | Specification |
|-----------|---------------|
| Form Factor | 2U Rack Barebones |
| Hypervisor | Proxmox VE |
| CPU | AMD Ryzen 7 5800G (8 Cores / 16 Threads) |
| GPU | AMD Radeon Vega 8 Integrated Graphics |
| Memory | 32 GB DDR5 6000 MHz |
| Motherboard | ASUS TUF B650M |
| Primary Storage | 500 GB PCIe Gen5 NVMe SSD |
| VM Storage | 2 TB PCIe Gen4 NVMe SSD |
| NAS Storage | 1 TB SATA SSD |
| Power Supply | Corsair Gold 800 W |
| CPU Cooler | Noctua NH-L9a Low Profile |

---

## Virtual Machine Resource Allocation

| Virtual Machine | vCPUs | RAM | Virtual Disk | Additional Storage | Primary Role |
|-----------------|:-----:|----:|-------------:|--------------------|--------------|
| Proxmox (Host) | 3 | 4 GB | 500 GB | — | Hypervisor Management |
| OPNsense | 2 | 4 GB | 100 GB | — | Firewall, Routing, NAT, VLANs |
| TrueNAS SCALE | 2 | 8 GB | 100 GB | 1 TB SATA SSD | SMB NAS & Storage Server |
| Windows Server 2022 | 3 | 4 GB | 100 GB | — | Active Directory & DNS |
| Ubuntu Server | 6 | 12 GB | 200 GB | — | Docker Host & Linux Services |

---

## Resource Summary

### CPU Allocation

| Resource | Threads (vCPUs) |
|----------|--------:|
| Total CPU Threads Available | 16 |
| Allocated to Virtual Machines | 13 |

> **Note:** vCPU allocation is based on logical CPU threads. Since not every VM utilizes its assigned vCPUs simultaneously

---

### Memory Allocation

| Resource | Capacity (GB) |
|----------|---------:|
| Total Installed Memory | 32  |
| Allocated to Virtual Machines | 28  |

> Memory allocations are static and can be adjusted later if workloads increase.

---


## Workload Distribution

| System | Responsibilities |
|--------|------------------|
| Proxmox VE | Hypervisor, VM Management |
| OPNsense | Firewall, NAT, Routing, VLAN Segmentation |
| Windows Server | Active Directory, DNS Services |
| TrueNAS SCALE | SMB File Shares, Network Storage |
| Ubuntu Server | Docker Containers, Linux Services |

---

## Planned Resource Expansion

Future infrastructure improvement plans cancelled due to global computer component shortages

---

Note-

*The Hypervisor Server originally had 64GB RAM, however a motherboard DIMM slot went out and I ended up selling two of the sticks of 16GB to a friend who was in need of the memory due to the ongoing chip shortage.* 

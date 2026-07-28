# Storage 

## Storage Overview

The homelab uses three separate storage devices to isolate the hypervisor, virtual machine storage, and network-attached storage (NAS). 

---

# Physical Storage

| Device | Capacity | Interface | Purpose |
|---------|----------|-----------|---------|
| SSD 1 | 500 GB | PCIe Gen5 NVMe | Proxmox VE Operating System |
| SSD 2 | 2 TB | PCIe Gen4 NVMe | Virtual Machine Storage |
| SSD 3 | 1 TB | SATA SSD | TrueNAS Storage Pool (SMB NAS) |

---

# Storage Layout

```text
500 GB PCIe Gen5 NVMe
└── Proxmox VE
    ├── Operating System
    ├── Configuration
    ├── ISO Images
    ├── VM Templates
    └── Backups 

2 TB PCIe Gen4 NVMe
├── OPNsense (100 GB)
├── TrueNAS SCALE (100 GB)
├── Windows Server 2022 (100 GB)
├── Ubuntu Server (200 GB)
└── Remaining Capacity (1.5 TB)
    ├── Future Virtual Machines

1 TB SATA SSD
└── TrueNAS Storage Pool
    ├── SMB Shares
    ├── User Files
    ├── VM Backups
    ├── Documents
    └── Shared Storage
```

---

# Current Virtual Disk Allocation

| Virtual Machine | Virtual Disk | Storage Location |
|-----------------|-------------:|------------------|
| OPNsense | 100 GB | 2 TB PCIe Gen4 NVMe |
| TrueNAS SCALE | 100 GB | 2 TB PCIe Gen4 NVMe |
| Windows Server 2022 | 100 GB | 2 TB PCIe Gen4 NVMe |
| Ubuntu Server | 200 GB | 2 TB PCIe Gen4 NVMe |

---

# TrueNAS Storage Pool

| Pool | Capacity | Purpose |
|------|---------:|---------|
| Main Pool | 1 TB | Centralized Network Storage |

---


# Storage Design Goals

- Separate the hypervisor operating system from virtual machine storage.
- Dedicate high-speed NVMe storage to virtual machine workloads.
- Isolate network storage on a dedicated SATA SSD managed by TrueNAS.
- Simplify backup, maintenance, and future storage expansion.
- Provide centralized SMB storage for Windows and Linux systems.

---

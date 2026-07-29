# Automatically Generated Firewall Rules

| Rule | Interface | Protocol | Source | Destination | Port | Purpose |
|------|-----------|----------|--------|-------------|------|---------|
| Default Deny / State Violation | All | Any | Any | Any | Any | Blocks invalid or state-violating traffic |
| RFC4890 ICMP Rule | IPv6 | ICMPv6 | Any | Any | Any | Required IPv6 Neighbor Discovery traffic |
| RFC4890 ICMP Rule | IPv6 | ICMPv6 | This Firewall | `fe80::/10`, `ff02::/16` | Any | IPv6 Link-Local communication |
| RFC4890 ICMP Rule | IPv6 | ICMPv6 | `fe80::/10` | `fe80::/10`, `ff02::/16` | Any | IPv6 Neighbor Discovery |
| RFC4890 ICMP Rule | IPv6 | ICMPv6 | `ff02::/16` | `fe80::/10` | Any | IPv6 Multicast communication |
| RFC4890 ICMP Rule | IPv6 | ICMPv6 | `::` | `ff02::/16` | Any | IPv6 multicast requirements |
| Block Port 0 | All | TCP/UDP | Any | Any | Port 0 | Drops invalid TCP/UDP traffic |
| Block Port 0 | All | TCP/UDP | Any | Any | Port 0 | Drops invalid TCP/UDP traffic |
| SSH Lockout Protection | All | TCP | SSH Lockout Table | This Firewall | 22 | Prevents administrator lockout |
| HTTPS Lockout Protection | All | TCP | SSH Lockout Table | This Firewall | 443 | Prevents administrator lockout |
| VirusProt Table | All | Any | VirusProt Table | Any | Any | Blocks known malicious IP addresses |
| DHCP Server Access | VLAN 2 | UDP | Any | 255.255.255.255 | 67 | DHCP Discover Broadcast |
| DHCP Server Access | VLAN 2 | UDP | Any | This Firewall | 67 | DHCP Requests |
| Firewall Self Traffic | Any | Any | Firewall | Any | Any | Allows firewall generated traffic |
| Anti-Lockout Rule | LAN | TCP | Any | This Firewall | 80 | HTTP Management Access |
| Anti-Lockout Rule | LAN | TCP | Any | This Firewall | 443 | HTTPS Management Access |

---

# Manual Firewall Rules

## Floating Rules

| Rule | Interface | Source | Destination | Protocol | Purpose |
|------|-----------|--------|-------------|----------|---------|
| Web GUI Access | Floating | 192.168.50.10 | Any | IPv4 | Allows management workstation access to the homelab |


## Interface Rules

| Interface | Source | Destination | Protocol | Purpose |
|-----------|--------|-------------|----------|---------|
| LAN | LAN Network | Any | Any | Default LAN outbound access |
| VLAN 10 | VLAN10 Network | Any | Any | Backend VLAN Internet access |
| VLAN 20 | VLAN20 Network | Any | Any | Frontend VLAN Internet access |

---

# NAT Rules (Outbound Hybrid Mode)

| Interface | Source Network | Destination | Translation | Purpose |
|-----------|----------------|-------------|-------------|---------|
| WAN | VLAN10 Network (192.168.10.0/24) | Any | WAN Interface Address | Allows Backend VLAN devices to access the Internet |
| WAN | VLAN20 Network (192.168.20.0/24) | Any | WAN Interface Address | Allows Frontend VLAN devices to access the Internet |

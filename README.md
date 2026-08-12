# office-network-vlan

a office network vlan made in CISCO packet tracer

<img width="1079" height="620" alt="image" src="https://github.com/user-attachments/assets/b036f745-4a50-48d4-b8fe-88b2fda521f0" />

## VLAN & Interface Addressing

| VLAN ID | Name | Subnet | Gateway IP | Router Interface |
|---|---|---|---|---|
| 10 | HR | 192.168.10.0/24 | 192.168.10.1 | Gi0/0.10 |
| 20 | Management | 192.168.20.0/24 | 192.168.20.1 | Gi0/1 |
| 30 | Guest | 192.168.30.0/24 | 192.168.30.1 | Gi0/0.30 |



## DHCP Pool Ranges

| Pool Name | VLAN | Usable Range | DNS Server |
|---|---|---|---|
| HR-POOL | 10 | 192.168.10.2 – 192.168.10.254 | 8.8.8.8 |
| MGMT-POOL | 20 | 192.168.20.2 – 192.168.20.254 | 8.8.8.8 |
| GUEST-POOL | 30 | 192.168.30.2 – 192.168.30.254 | 8.8.8.8 |



## Physical / Trunk Links

| Link | Type | VLANs Carried |
|---|---|---|
| Router Gi0/0 ↔ Switch1 (HR) | Trunk | 10, 30 |
| Router Gi0/1 ↔ Switch0 (Management) | Access | 20 |
| Switch1 ↔ Switch2 (Guest) | Trunk | 10, 30 |



## ACLs — Guest Isolation

| ACL # | Applied On | Source | Destination | Action |
|---|---|---|---|---|
| 110 | Gi0/0.10 | 192.168.10.0/24 | 192.168.30.0/24 | Deny |
| 120 | Gi0/1 | 192.168.20.0/24 | 192.168.30.0/24 | Deny |
| 130 | Gi0/0.30 | 192.168.30.0/24 | 192.168.10.0/24, 192.168.20.0/24 | Deny |


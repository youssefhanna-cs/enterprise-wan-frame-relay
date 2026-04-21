# 🌐 IP Addressing Plan

## WAN Network (Frame Relay Cloud)

| Router | Interface | IP Address | DLCI |
|--------|-----------|------------|------|
| Cairo | Se0/1/0 | 10.10.10.1/8 | 100, 200, 300 |
| Alexandria | Se0/1/0 | 10.10.10.2/8 | 400, 500, 600 |
| Giza | Se0/1/0 | 10.10.10.3/8 | 700, 800, 900 |
| Damietta | Se0/1/0 | 10.10.10.4/8 | 40, 50, 60 |

---

## Cairo Branch (RIP + OSPF)

| Device | Interface | IP Address | Network |
|--------|-----------|------------|---------|
| Cairo Router | Gi0/0 | 60.0.0.1/24 | RIP |
| Cairo Router | Gi0/1 | 70.0.0.3/24 | RIP |
| Redistribution Router | Gi0/0 | 50.0.0.2/24 | OSPF |
| Redistribution Router | Gi0/1 | 60.0.0.1/24 | RIP |
| Edge Router | Se0/1/0 | 10.10.10.1/8 | WAN |
| Edge Router | Gi0/0 | 50.0.0.1/24 | OSPF |
| PC0 | Fa0 | 70.0.0.2/24 | — |
| PC1 | Fa0 | 70.0.0.1/24 | — |

---

## Damietta Branch (OSPF)

| Device | Interface | IP Address | Network |
|--------|-----------|------------|---------|
| Damietta Router | Gi0/0 | 40.0.0.3/24 | OSPF |
| Damietta Router | Se0/1/0 | 10.10.10.4/8 | WAN |
| PC2 | Fa0 | 40.0.0.2/24 | — |
| PC3 | Fa0 | 40.0.0.1/24 | — |

---

## Alexandria Branch (EIGRP AS5 + EIGRP AS8 + VLANs)

| Device | Interface | IP Address | Network |
|--------|-----------|------------|---------|
| Edge Router | Se0/1/0 | 10.10.10.2/8 | WAN |
| Edge Router | Gi0/0 | 20.0.0.1/24 | EIGRP AS5 |
| Redistribution Router | Gi0/0 | 20.0.0.2/24 | EIGRP AS5 |
| Redistribution Router | Gi0/1 | 30.0.0.1/24 | EIGRP AS8 |
| Alex Router (R-on-a-Stick) | Gi0/0 | 30.0.0.2/24 | EIGRP AS8 |
| Alex Router | Gi0/1.10 | 192.168.5.2/24 | VLAN 10 |
| Alex Router | Gi0/1.20 | 192.168.6.2/24 | VLAN 20 |
| PC4 | Fa0 | 192.168.5.1/24 | VLAN 10 |
| PC5 | Fa0 | 192.168.6.1/24 | VLAN 20 |

---

## Giza Branch (OSPF + EIGRP AS9)

| Device | Interface | IP Address | Network |
|--------|-----------|------------|---------|
| Edge+Redist Router | Se0/1/0 | 10.10.10.3/8 | WAN |
| Edge+Redist Router | Gi0/0 | 90.0.0.1/24 | EIGRP AS9 |
| Edge+Redist Router | Gi0/1 | 80.0.0.1/24 | OSPF |
| Giza Router-1 | Gi0/0 | 90.0.0.2/24 | EIGRP AS9 |
| Giza Router-1 | Gi0/1 | 192.168.2.3/24 | — |
| Giza Router-2 | Gi0/0 | 80.0.0.2/24 | OSPF |
| Giza Router-2 | Gi0/1 | 192.168.1.3/24 | — |
| PC6 | Fa0 | 192.168.2.2/24 | — |
| PC7 | Fa0 | 192.168.2.1/24 | — |
| PC8 | Fa0 | 192.168.1.1/24 | — |
| PC9 | Fa0 | 192.168.1.2/24 | — |

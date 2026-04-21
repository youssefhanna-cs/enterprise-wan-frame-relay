# 📋 Project Scenario

## 🏢 Business Context

**TechCorp Egypt** is a mid-sized technology company operating across four cities in Egypt. The company has its headquarters in **Cairo** and regional branches in **Damietta**, **Alexandria**, and **Giza**.

Each branch was built independently over the years, resulting in a heterogeneous network environment where different routing protocols are in use at each location.

---

## ❗ Problem Statement

The company needs a **unified WAN infrastructure** that:
- Connects all four branches securely
- Preserves existing routing protocols at each branch (no full migration)
- Allows full communication between all branches
- Enforces a specific security policy restricting certain inter-branch traffic

---

## 🎯 Solution

As the network engineer, the solution was to:

1. **Deploy a Frame Relay WAN** using a simulated ISP Cloud to interconnect all branches in a **Hub-and-Spoke** topology, with **Cairo as the Hub**
2. **Maintain existing routing protocols** per branch:
   - Cairo: RIP (internal LAN) + OSPF (toward WAN edge)
   - Damietta: OSPF
   - Alexandria: EIGRP AS8 (LAN) + EIGRP AS5 (toward WAN edge)
   - Giza: EIGRP AS9 (LAN) + OSPF (LAN)
3. **Implement Route Redistribution** at boundary routers to ensure full reachability across all protocol domains
4. **Segment the Alexandria branch** using VLANs (VLAN 10 & VLAN 20) with Router-on-a-Stick for inter-VLAN routing
5. **Apply an ACL** on the Cairo edge router to block specific unauthorized traffic between branches

---

## 🔐 Security Policy

> **Rule:** Deny all traffic from **PC0 (70.0.0.1)** in the Cairo branch to **PC3 (40.0.0.1)** in the Damietta branch.
> All other inter-branch traffic is permitted.

---

## 📍 Branch Summary

| Branch | Role | Internal Protocol | WAN IP |
|--------|------|-------------------|--------|
| Cairo | Hub (HQ) | RIP + OSPF | 10.10.10.1 |
| Damietta | Spoke | OSPF | 10.10.10.4 |
| Alexandria | Spoke | EIGRP AS5 + AS8 | 10.10.10.2 |
| Giza | Spoke | OSPF + EIGRP AS9 | 10.10.10.3 |

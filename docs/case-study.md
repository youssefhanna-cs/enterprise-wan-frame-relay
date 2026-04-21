# 🌐 Enterprise WAN Case Study
## Frame Relay & Multi-Protocol Routing Integration

---

## 📌 Executive Summary
This project demonstrates the design and implementation of a multi-branch enterprise WAN connecting four geographically distributed locations using Frame Relay technology.

The network integrates multiple routing protocols (RIP, OSPF, EIGRP) and ensures full connectivity through route redistribution while applying basic traffic control policies.

---

## 🏢 Business Scenario
A company operates four branches across Egypt:
- Cairo
- Alexandria
- Giza
- Damietta

Due to legacy infrastructure, each branch uses a different routing protocol. The company requires:
- Full connectivity between all branches  
- Preservation of existing routing protocols  
- Secure and controlled communication  

---

## 🎯 Objectives
- Design a scalable WAN architecture  
- Integrate multiple routing protocols  
- Implement route redistribution  
- Apply traffic control using ACL  
- Validate full end-to-end connectivity  

---

## 🧩 Network Architecture

### WAN Design
- Technology: Frame Relay (ISP simulation)  
- WAN Network: 10.10.10.0/8  
- Full Mesh connectivity — direct PVC between every pair of branches

---

### Routing Design

| Branch      | Protocol |
|------------|---------|
| Cairo      | RIP +  OSPF   |
| Damietta   | OSPF    |
| Alexandria | EIGRP + EIGRP  |
| Giza       | OSPF + EIGRP |

---

### Key Features
- Multi-protocol routing environment  
- Route redistribution between protocols  
- VLAN segmentation (Alexandria)  
- Access Control List (ACL) implementation  

---

## 🔁 Route Redistribution Strategy

To ensure interoperability between routing domains:

- RIP ↔ OSPF (Cairo Router)  
- EIGRP 5 ↔ EIGRP 8 (Alex Router) 
- OSPF ↔ EIGRP (Giza Router)  

### Outcome
All networks are reachable regardless of protocol boundaries.

---

## 🔐 Security Implementation

An ACL was applied to restrict unauthorized traffic:

- Blocked:
  - Source: 70.0.0.1  
  - Destination: 40.0.0.1  

### Purpose
- Simulate basic security policy  
- Demonstrate traffic filtering capability  

---

## 🧪 Verification & Testing

### Routing Validation
Command:
show ip route

Result:
- R (RIP), O (OSPF), D (EIGRP) routes present  

✔ Confirms successful redistribution  

---

### WAN Validation
Commands:
show frame-relay map
show frame-relay pvc

✔ Active connections confirmed  

---

### Connectivity Testing

| Test Case | Result |
|----------|-------|
| Allowed Traffic | ✅ Success |
| Blocked Traffic | ❌ Denied |

---

## ⚠️ Challenges

- Complexity of route redistribution  
- Avoiding routing loops  
- Frame Relay configuration accuracy  
- Ensuring protocol interoperability  

---

## ✅ Solutions

- Careful metric configuration  
- Incremental testing  
- Validation using routing tables  
- Structured network design  

---

## 📊 Results

- Full connectivity achieved across all branches  
- Stable routing environment  
- Secure traffic control applied  
- Successful WAN simulation  

---

## 🧠 Key Learnings

- Real-world WAN design concepts  
- Multi-protocol routing integration  
- Importance of route redistribution  
- Network validation and troubleshooting  

---

## 🚀 Conclusion

This project demonstrates a practical implementation of enterprise WAN design, integrating heterogeneous routing protocols into a unified network.

It reflects real-world scenarios where legacy systems must coexist within modern network architectures while maintaining performance, scalability, and security.

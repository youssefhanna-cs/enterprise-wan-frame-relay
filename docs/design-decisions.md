# 🧠 Design Decisions

## 1. Frame Relay — Why Hub-and-Spoke?

Frame Relay was chosen to simulate a real ISP WAN service. The **Hub-and-Spoke** topology was selected because:
- Cairo (HQ) acts as the central communication point
- Reduces the number of PVCs needed (N-1 instead of N*(N-1)/2 for full mesh)
- Reflects real-world ISP cost structures where full mesh is expensive

**Tradeoff:** Spoke-to-spoke traffic must pass through the Hub, adding latency — acceptable for this scenario.

---

## 2. Multi-Protocol Routing — Why Not Standardize?

Each branch uses a different routing protocol to simulate **legacy enterprise environments** where migrating all branches to a single protocol is not always feasible. This reflects real-world scenarios where:
- RIP may exist in older Cairo infrastructure
- OSPF is preferred for the WAN backbone (scalable, fast convergence)
- EIGRP is used in branches originally managed by Cisco-centric teams

---

## 3. Route Redistribution — Boundary Routers

Redistribution was implemented **only at boundary routers** (not throughout the network) to:
- Minimize the risk of routing loops
- Keep routing domains isolated and manageable
- Allow each branch to maintain its own routing policy

---

## 4. Alexandria VLANs — Router-on-a-Stick vs. L3 Switch

**Router-on-a-Stick** was chosen over a Layer 3 switch because:
- Simpler to configure in Packet Tracer for learning purposes
- Demonstrates the concept of subinterfaces and 802.1Q encapsulation clearly
- A Layer 3 switch would be preferred in production for performance

---

## 5. ACL Placement — Cairo Outbound

The ACL was applied **outbound on Cairo's WAN-facing interface** because:
- Traffic from PC0 exits through Cairo toward Damietta
- Outbound filtering prevents the traffic from entering the WAN
- Applying inbound on Damietta's interface would also work but is less efficient (traffic already traversed the WAN)

---

## 6. Layer 2 Security on All Switches

**Port Security + BPDU Guard + PortFast + RSTP** were applied on all access switches because:
- Port Security limits MAC flooding attacks
- BPDU Guard protects against rogue switches on access ports
- PortFast + RSTP speeds up host connectivity
- Consistent security baseline across all branches

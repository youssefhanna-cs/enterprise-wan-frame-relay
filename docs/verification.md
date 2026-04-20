# ✅ Verification & Testing

## 🔍 Commands Used

### Frame Relay Verification
```
show frame-relay map
show frame-relay pvc
show interfaces serial 0/1/0
```

### Routing Table Verification
```
show ip route
```
Expected output includes:
- `R` — RIP routes (Cairo branch)
- `O` — OSPF routes (Cairo ↔ Damietta ↔ Giza)
- `D` — EIGRP routes (Alexandria ↔ Giza)
- `O E2` / `D EX` — Redistributed routes across protocol boundaries

### Redistribution Verification
```
show ip route
show ip protocols
```

### ACL Verification
```
show access-lists
show ip interface
```

---

## 🧪 Test Cases

| Test | Source | Destination | Expected Result |
|------|--------|-------------|----------------|
| Cross-branch reachability | PC7 (Giza) | PC2 (Damietta) | ✅ Success |
| Cross-branch reachability | PC6 (Giza) | PC3 (Damietta) | ✅ Success |
| ACL block | PC0 (70.0.0.1) | PC3 (40.0.0.1) | ❌ Denied |
| ACL allow | PC1 (70.0.0.2) | PC3 (40.0.0.1) | ✅ Success |
| VLAN inter-routing | PC4 (VLAN10) | PC5 (VLAN20) | ✅ Success |

---

## 📸 Screenshots

### Frame Relay Maps
- Cairo: `screenshots/frame-relay/frame-relay-map-in-cairo.png`
- Alexandria: `screenshots/frame-relay/frame-relay-map-in-alex.png`
- Damietta: `screenshots/frame-relay/frame-relay-map-in-damietta.png`
- Giza: `screenshots/frame-relay/frame-relay-map-in-giza.png`

### Redistribution
- RIP ↔ OSPF (Cairo): `screenshots/redistribution/redistribution-rip-ospf-in-cairo.png`
- EIGRP ↔ EIGRP (Alex): `screenshots/redistribution/redistribution-eigrp-eigrp-in-alex.png`
- EIGRP ↔ OSPF (Giza): `screenshots/redistribution/redistribution-eigrp-ospf-in-giza.png`

### ACL
- ACL applied in Cairo: `screenshots/acl/acl-in-cairo.png`

### Ping Tests
- Successful ping: `screenshots/ping/ping-success.png`
- Blocked ping (ACL): `screenshots/ping/ping-blocked.png`

### VLANs
- Router-on-a-Stick config: `screenshots/vlans/vlan-router-on-stick.png`

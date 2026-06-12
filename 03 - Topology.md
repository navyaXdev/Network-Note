---
tags:
  - network/basic_of_network/Topology
---

# Network Topology

Network topology describes **how devices are connected** in a network.

| Type | Meaning |
|---|---|
| **Physical Topology** | The actual physical layout of cables and devices |
| **Logical Topology** | How data flows through the network (may differ from physical) |

---

## Types of Topology — Quick Comparison

| Topology | Shape | Fault Tolerance | Cost | Best For |
|---|---|---|---|---|
| Bus | Line | Low | Low | Small/old networks |
| Star | Star | Medium | Medium | Home, offices |
| Ring | Circle | Medium | Medium | Old LANs (Token Ring) |
| Mesh | Web | Very High | High | Critical networks |
| Hybrid | Mixed | High | High | Large enterprises |
| Point-to-Point | Direct link | Low | Low | Two devices/sites |
| Point-to-Multipoint | Hub + spokes | Medium | Medium | ISP, wireless |
| Spine-Leaf | Two-layer grid | Very High | High | Data centers |

---

## Bus Topology

All devices connect to a **single main cable** called the **backbone cable**, which has **terminators at both ends**.  
All devices share this one cable to communicate.

```
[T]──[PC1]──[PC2]──[PC3]──[PC4]──[T]
      backbone cable
T = Terminator
```

### ✅ Advantages
- Simple and cheap to set up
- Requires less cable than other topologies

### ❌ Disadvantages
- If the backbone cable fails, the **entire network goes down**
- Performance drops as more devices are added
- Difficult to troubleshoot
- **Obsolete** — rarely used in modern networks

---

## Star Topology

All devices connect to a **central device** (switch or hub).  
Most common topology in modern networks.

```
       [PC1]
         |
[PC2]──[SWITCH]──[PC3]
         |
       [PC4]
```

### ✅ Advantages
- Easy to add or remove devices
- One device fails → rest of the network keeps working
- Easy to troubleshoot

### ❌ Disadvantages
- If the **central switch/hub fails**, entire network goes down
- Requires more cable than bus topology

> 💡 Your home Wi-Fi router is the "star center" — all your devices connect to it.

---

## Ring Topology

Each device connects to **exactly two other devices**, forming a **closed circular loop**.  
Data travels from one device to the next around the ring until it reaches the destination.

```
[PC1]──[PC2]
  |          |
[PC4]──[PC3]
```

### ✅ Advantages
- Equal access for all devices
- Predictable performance under load

### ❌ Disadvantages
- If **one device or cable fails**, the entire ring can break (unless dual-ring is used)
- Slower than star for large networks
- Difficult to troubleshoot

---

## Mesh Topology

Every device is connected to **every other device**, creating many redundant paths.

**Full Mesh:** Every device connects to every other device.  
**Partial Mesh:** Some devices connect to all, others connect to only a few.

```
[PC1]───[PC2]
  |  ╲ ╱  |
  |  ╱ ╲  |
[PC4]───[PC3]
```

**Formula for full mesh connections:** `n(n-1)/2`  
(e.g., 4 devices = 4×3/2 = **6 connections**)

### ✅ Advantages
- Highest fault tolerance — multiple paths available
- No single point of failure
- High performance and reliability

### ❌ Disadvantages
- Very expensive — lots of cables and ports needed
- Complex to set up and manage

> 💡 Used in critical infrastructure — military networks, financial systems, internet backbone.

---

## Hybrid Topology

Combines **two or more different topologies** into one network.  
The **most commonly used** topology in modern large networks.

```
[Star LAN] ──── [Ring backbone] ──── [Star LAN]
```

### ✅ Advantages
- Flexible — combine the best of each topology
- Scalable — easy to add new segments
- Reliable — faults in one segment don't affect others

### ❌ Disadvantages
- Complex design and management
- Higher cost

> 💡 A large university might use star topology in each building, connected together via a ring or mesh backbone.

---

## Point-to-Point Topology

A **direct dedicated connection** between exactly **two devices** (routers, switches, computers).

```
[Router A] ————————— [Router B]
```

### ✅ Advantages
- Simple and fast
- Dedicated bandwidth — no sharing

### ❌ Disadvantages
- Not scalable — only two devices
- Expensive for long distances

---

## Point-to-Multipoint Topology

One **central device** connects to **multiple other devices** — also called a **one-to-many** connection.

```
         [Central Device]
        /        |        \
   [Device1] [Device2] [Device3]
```

### ✅ Advantages
- Cost-effective — one central device serves many
- Common in wireless/ISP networks

### ❌ Disadvantages
- Central device is a single point of failure
- Bandwidth is shared among all connected devices

---

## Spine-Leaf Topology

A **modern two-layer data center architecture** where every leaf switch connects to every spine switch.  
Designed for **east-west traffic** (server-to-server communication inside a data center).

```
SPINE LAYER:   [Spine 1] ─── [Spine 2]
                /   \           /   \
              /       \       /       \
LEAF LAYER: [Leaf1] [Leaf2] [Leaf3] [Leaf4]
              |        |       |        |
           [Srv]    [Srv]   [Srv]    [Srv]
```

### Two Layers

| Layer | Switch Type | Role |
|---|---|---|
| **Core** | Spine Switches | Connect all leaf switches to each other |
| **Access** | Leaf Switches | Connect to servers and end devices |

### How Traffic Flows

Maximum **2 hops** for any server-to-server communication:
1. Device → Leaf switch
2. Leaf → Spine switch
3. Spine → Destination Leaf switch

### ✅ Advantages
- **Low latency** — fixed, predictable path (max 2 hops)
- **High redundancy** — multiple paths between any two devices
- **No bottlenecks** — unlike traditional 3-tier core/distribution/access design
- **Easy horizontal scaling** — just add more leaf/spine switches

### ❌ Disadvantages
- More cabling required
- Higher cost
- More complex design than traditional architectures

> 💡 Used by hyperscalers like Google, Facebook, Amazon in their massive data centers.

---

## [[04 - MODEL]]

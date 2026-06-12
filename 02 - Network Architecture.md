---
tags:
  - network/basic_of_network/Architecture
---

# Network Architecture

Network architecture defines **how devices are organized and communicate** in a network.  
The two fundamental types are **Peer-to-Peer** and **Client-Server**.

---

## Quick Comparison

| Feature | Peer-to-Peer (P2P) | Client-Server |
|---|---|---|
| Central server | ❌ No | ✅ Yes |
| Security | Weak | Strong |
| Cost | Low | High |
| Management | Difficult at scale | Easy (centralized) |
| Best for | Small networks (2–10 devices) | Medium to large networks |
| Example | Home file sharing | Corporate office, school |

---

## Peer-to-Peer (P2P)

A network where **all computers are equal** — there is no central server.  
Each computer can act as both a client (requests resources) and a server (provides resources).

```
[PC 1] ←——→ [PC 2]
   ↕               ↕
[PC 3] ←——→ [PC 4]
```

### Key Features
- No central server
- All computers have equal authority
- Each computer manages its own security
- Resources shared directly between computers

### ✅ Advantages
- Easy to set up
- Low cost — no dedicated server hardware needed
- Simple for small networks

### ❌ Disadvantages
- Poor security — each device manages itself
- Hard to manage as the network grows
- Difficult backup management — no central storage
- Not suitable for large networks

> 💡 **Real-world example:** Sharing files between two laptops on the same Wi-Fi, or BitTorrent file sharing.

---

## Client-Server

A network where a **central server controls resources, security, and access**.  
Clients (computers/devices) send requests — the server responds.

```
        [SERVER]
       /    |    \
   [PC1] [PC2] [PC3]
```

### Key Features
- Centralized control
- Dedicated server manages the network
- Centralized security policies
- Easier management through the server

### ✅ Advantages
- Strong security — policies enforced centrally
- Easy and centralized backup
- Easy to manage even with many users
- Supports many users simultaneously
- Better and consistent performance

### ❌ Disadvantages
- Higher cost — requires dedicated server hardware
- Requires a network administrator
- If server goes down, the whole network is affected (**single point of failure**)

> 💡 **Real-world example:** A school or company where all files, logins, and permissions are managed by a central server.

---

## Which One to Choose?

| Situation | Recommended |
|---|---|
| Home, 2–5 devices, casual sharing | Peer-to-Peer |
| Small office, 6–10 devices | Peer-to-Peer |
| Medium/large office, 10+ devices | Client-Server |
| Security and centralized control needed | Client-Server |
| Tight budget, simple needs | Peer-to-Peer |

---

## [[03 - Topology]]

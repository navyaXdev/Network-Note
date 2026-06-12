---
tags:
  - network/model
---

# OSI Model

The **OSI (Open Systems Interconnection)** model is a **7-layer framework** that standardizes how network communication works — from physical cables to the software applications we use.

> 💡 It describes how data travels from a software application on one computer, through the network, to reach software on another computer.

**Memory trick (top to bottom):** **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

---

## The 7 Layers

| Layer | Name | Data Unit | Key Devices |
|---|---|---|---|
| 7 | Application | Data | Browser, App |
| 6 | Presentation | Data | SSL/TLS, Codecs |
| 5 | Session | Data | NetBIOS, RPC |
| 4 | Transport | Segment | Firewall |
| 3 | Network | Packet | Router, L3 Switch |
| 2 | Data Link | Frame | Switch, Bridge |
| 1 | Physical | Bits | Cable, NIC, Hub |

---

## Layer 1 — Physical Layer

Deals with **raw bit transmission** through physical media — cables, connectors, signals.

- Defines electrical signals, voltage levels, cable types, and pin layouts
- Devices: **Cables, Network Interface Cards (NICs), Hubs, Repeaters**
- Data unit: **Bits (0s and 1s)**

> 💡 Think of it as the "road" — it just carries traffic, doesn't care what's in it.

---

## Layer 2 — Data Link Layer

Takes raw bits from Layer 1 and organizes them into **frames**.  
Responsible for **node-to-node** communication on the same network.

- Adds **MAC addresses** to identify source and destination on the local network
- Error detection using **CRC (Cyclic Redundancy Check)** in the trailer
- Devices: **Switches, Bridges**
- Data unit: **Frame**

### Ethernet Frame Structure

```
| MAC DEST  | MAC SOURCE | EtherType | PAYLOAD (Data) | FCS (CRC) |
| 6 bytes   | 6 bytes    | 2 bytes   | 46–1500 bytes  | 4 bytes   |
```

### MAC Address

- A **unique hardware identifier** assigned to every network interface card (NIC)
- Written as: `20:12:C3:54:B3:13` (6 pairs of hex digits)
- First 3 pairs = **OUI** (manufacturer ID) | Last 3 pairs = **device ID**
- Switches use MAC addresses to decide **where to forward frames**
- MAC addresses work only within the **same local network**

---

## Layer 3 — Network Layer

Responsible for **routing packets** across different networks using **IP addresses**.

- Breaks data into **packets** and adds IP header with source/destination IP
- Determines the **best path** to the destination
- Devices: **Routers, Layer 3 Switches**
- Data unit: **Packet**

### Packet Structure (simplified)

```
| IP HEADER      | MAC HEADER        | PAYLOAD  | TRAILER |
| 12.34.56.78    | 20:12:C3:54:B3:13 | data...  |         |
```

> 💡 **MAC address** = local delivery (within LAN). **IP address** = global routing (across networks). Both are needed.

---

## Layer 4 — Transport Layer

Provides **end-to-end communication** between applications on different hosts.  
Uses **port numbers** to identify which application the data belongs to.

| Feature | TCP | UDP |
|---|---|---|
| Full Name | Transmission Control Protocol | User Datagram Protocol |
| Reliability | ✅ Guaranteed delivery | ❌ No guarantee |
| Error checking | ✅ Yes | ✅ Basic |
| Order | ✅ Reassembles in order | ❌ No ordering |
| Speed | Slower | Faster |
| Use case | Web, Email, File Transfer | Video streaming, Gaming, DNS |

> 💡 **TCP** = registered post (confirmed delivery). **UDP** = dropping a flyer in a letterbox (fast, no confirmation).

---

## Layer 5 — Session Layer

Controls the **dialogue** between two communicating devices.

- Responsible for **starting, managing, and ending** communication sessions
- Handles **authentication** and **reconnection** if a session drops
- Also called the **traffic cop** of the network
- Examples: NetBIOS, RPC, PPTP

> 💡 When you're on a video call, the session layer manages that "conversation" — it tracks who is talking to whom and for how long.

---

## Layer 6 — Presentation Layer

Responsible for **translating data** into a format the application layer can understand.  
Also called the **translation layer**.

- **Encoding/Decoding** — converts character sets (e.g., ASCII ↔ Unicode)
- **Compression/Decompression** — reduces data size
- **Encryption/Decryption** — secures data (e.g., SSL/TLS)
- Examples: JPEG, MP3, MPEG, SSL

> 💡 Think of it as a translator — it makes sure both sides "speak the same language."

---

## Layer 7 — Application Layer

The layer **users interact with directly** — the interface between the network and the application.

- Provides network services to applications (not the app itself, but the protocols apps use)
- Examples: **HTTP, HTTPS, FTP, SMTP, DNS, DHCP**

> 💡 When you open a browser and visit a website, you're interacting with Layer 7.

---

## OSI Data Units Summary

```
Application  →  Data
Transport    →  Segment
Network      →  Packet
Data Link    →  Frame
Physical     →  Bits
```

---

# TCP/IP Model

The **TCP/IP (Transmission Control Protocol / Internet Protocol)** model is the practical model actually used on the internet. It has **4 layers** (a simplified version of OSI).

| Layer | Function | OSI Equivalent |
|---|---|---|
| **Application** | User interaction and services | Layers 5, 6, 7 |
| **Transport** | End-to-end communication | Layer 4 |
| **Internet** | Routing and IP addressing | Layer 3 |
| **Network Access** | Physical network communication | Layers 1, 2 |

---

## OSI vs TCP/IP Mapping

```
OSI Model          TCP/IP Model
─────────────      ─────────────────
7 Application  ┐
6 Presentation ├──► Application
5 Session      ┘
4 Transport    ───► Transport
3 Network      ───► Internet
2 Data Link    ┐
1 Physical     ┘──► Network Access
```

---

# Encapsulation & Decapsulation

## Encapsulation (Sending Data — Going DOWN the layers)

Each layer **adds its own header** (and sometimes trailer) to the data as it passes down.

```
Step 1 — Application Layer:    [DATA]
Step 2 — Transport Layer:      [TCP HEADER | DATA]
Step 3 — Network Layer:        [IP HEADER | TCP HEADER | DATA]
Step 4 — Data Link Layer:      [MAC HEADER | IP HEADER | TCP HEADER | DATA | FCS]
Step 5 — Physical Layer:       101010100111001... (bits over the wire)
```

## Decapsulation (Receiving Data — Going UP the layers)

Each layer **removes its own header** and passes the remaining data up.

```
Physical   → reads bits
Data Link  → removes MAC header/trailer → checks for errors
Network    → removes IP header → checks destination IP
Transport  → removes TCP header → reassembles segments
Application → receives the original data
```

> 💡 Think of encapsulation like putting a letter in envelopes — each layer adds a new envelope. Decapsulation is opening each envelope one by one.

---

## [[05 - IP Address]]

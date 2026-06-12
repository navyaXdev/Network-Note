---
tags:
  - network/ip_address
---

# IP Address

## What is an IP Address?

An **IP (Internet Protocol) address** is a **logical address** assigned to a device on a network.  
Unlike a MAC address (which is hardware-based and fixed), an IP address is **software-based** and can change.

**It is used to:**
- **Identify** devices on a network
- **Locate** devices (which network they're on)
- **Allow communication** between devices across networks

> 💡 Think of an IP address like your **home address** — it tells the network exactly where to deliver data.

---

## IP Address Versions

| Version | Example | Length | Status |
|---|---|---|---|
| **IPv4** | `192.168.1.1` | 32 bits | Still most common |
| **IPv6** | `2001:0db8:85a3::8a2e:0370:7334` | 128 bits | Newer, replacing IPv4 |

---

# IPv4

## Structure of an IPv4 Address

- **32 bits** long, divided into **4 octets** (groups of 8 bits), separated by dots.
- Each octet ranges from **0 to 255**.

```
192   .   168   .   1   .   1
 ↑         ↑        ↑      ↑
8 bits   8 bits  8 bits  8 bits
        Total = 32 bits
```

**Binary example:**
```
192.168.1.1
= 11000000.10101000.00000001.00000001
```

---

## Two Parts of an IP Address

Every IP address has two parts:

| Part | Purpose |
|---|---|
| **Network ID** | Identifies which network the device is on |
| **Host ID** | Identifies the specific device on that network |

> 💡 Like a phone number: **area code** (network) + **number** (host)

---

## IPv4 Address Classes

Originally, IP addresses were divided into **classes** based on their first octet.

| Class | Range | Default Subnet Mask | Used For |
|---|---|---|---|
| **A** | 1.0.0.0 – 126.255.255.255 | 255.0.0.0 /8 | Large networks |
| **B** | 128.0.0.0 – 191.255.255.255 | 255.255.0.0 /16 | Medium networks |
| **C** | 192.0.0.0 – 223.255.255.255 | 255.255.255.0 /24 | Small networks |
| **D** | 224.0.0.0 – 239.255.255.255 | — | Multicast |
| **E** | 240.0.0.0 – 255.255.255.255 | — | Reserved/Research |

> ⚠️ **127.x.x.x** is reserved for **loopback** (your own device — `127.0.0.1` = "localhost")

---

## Public vs Private IP Addresses

| Type | Description | Who can see it? |
|---|---|---|
| **Public IP** | Assigned by ISP, unique on the internet | Everyone on the internet |
| **Private IP** | Used inside local networks, not routable on internet | Only within your network |

### Private IP Ranges (RFC 1918)

| Class | Private Range | Common Use |
|---|---|---|
| A | `10.0.0.0 – 10.255.255.255` | Large enterprises |
| B | `172.16.0.0 – 172.31.255.255` | Medium networks |
| C | `192.168.0.0 – 192.168.255.255` | Home/small office |

> 💡 Your home router gives devices private IPs (e.g. `192.168.1.x`). Your router's **public IP** is what the internet sees.

---

## Subnet Mask

A subnet mask tells the network **which part of the IP is the network ID and which part is the host ID**.

```
IP Address:    192.168.1.10
Subnet Mask:   255.255.255.0

Network part:  192.168.1   (first 3 octets)
Host part:              10  (last octet)
```

### CIDR Notation (Classless Inter-Domain Routing)

Instead of writing the full subnet mask, we use a `/` followed by the number of network bits.

```
192.168.1.10/24   →   subnet mask: 255.255.255.0  (24 bits for network)
10.0.0.1/8        →   subnet mask: 255.0.0.0       (8 bits for network)
172.16.0.1/16     →   subnet mask: 255.255.0.0     (16 bits for network)
```

---

## Special IP Addresses

| Address | Purpose |
|---|---|
| `127.0.0.1` | Loopback — refers to your own device ("localhost") |
| `0.0.0.0` | Unspecified address — used during DHCP discovery |
| `255.255.255.255` | Limited broadcast — sends to all devices on local network |
| `169.254.x.x` | APIPA — auto-assigned when DHCP server is unreachable |

---

## Static vs Dynamic IP

| Type | Description | Use Case |
|---|---|---|
| **Static** | Manually assigned, never changes | Servers, printers, routers |
| **Dynamic** | Automatically assigned by DHCP, can change | Most client devices |

### DHCP (Dynamic Host Configuration Protocol)

When your device joins a network, it asks a **DHCP server** for an IP address automatically.  
The server assigns: IP address, Subnet mask, Default gateway, DNS server

---

# IPv6

## Why IPv6?

IPv4 only supports ~**4.3 billion** addresses — nearly exhausted.  
IPv6 supports **340 undecillion** addresses (3.4 × 10³⁸) — practically unlimited.

## IPv6 Structure

- **128 bits** long, written as **8 groups of 4 hex digits**, separated by colons.

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

**Shortening rules:**
1. Remove leading zeros in each group: `0db8` → `db8`
2. Replace one group of consecutive all-zero groups with `::` (only once)

```
Full:       2001:0db8:0000:0000:0000:0000:0370:7334
Shortened:  2001:db8::370:7334
```

## IPv6 Address Types

| Type | Description |
|---|---|
| **Unicast** | One-to-one (one sender, one receiver) |
| **Multicast** | One-to-many (sends to a group) |
| **Anycast** | One-to-nearest (sends to the nearest device in a group) |

> ⚠️ IPv6 has **no broadcast** — replaced by multicast.


# What is a Network?

A network is **two or more connected systems** that can share resources such as data, applications, and internet connections.

> 💡 Your home Wi-Fi is a network — your phone, laptop, and TV all share the same internet connection.

---

## Types of Network

| Type   | Full Name                 | Coverage Area    | Example                      |
| ------ | ------------------------- | ---------------- | ---------------------------- |
| PAN    | Personal Area Network     | Few meters       | Bluetooth, USB               |
| LAN    | Local Area Network        | Building / Floor | Home, School, Office         |
| CAN    | Campus Area Network       | Campus / Complex | University, Corporate campus |
| MAN    | Metropolitan Area Network | City             | City-wide ISP network        |
| WAN    | Wide Area Network         | Country / World  | The Internet                 |
| SAN    | Storage Area Network      | Data Center      | Enterprise storage           |
| SD-WAN | Software-Defined WAN      | Any WAN          | Cloud-managed branches       |

---

### 🔵 PAN — Personal Area Network

- Connects personal devices within a **very short distance** (a few meters) around a person.
- Devices: phone, laptop, smartwatch, earbuds, etc.
- Technologies: **Bluetooth**, USB, Infrared

---

### 🟢 LAN — Local Area Network

- Connects computers and devices within a **limited geographic area** (a building or floor).
- Fastest and most secure type of network.
- Technologies: **Ethernet**, Wi-Fi
- Examples: Home network, school computer lab, office floor

---

### 🟡 CAN — Campus Area Network

- Connects **multiple LANs** within a limited area like a college campus, university, or corporate complex.
- Allows different buildings on the campus to communicate with each other.
- Larger than a LAN but smaller than a MAN.

---

### 🟠 MAN — Metropolitan Area Network

- Covers a **city or metropolitan area** and connects multiple LANs together.
- Owned by ISPs (Internet Service Providers) or city governments.
- Example: Cable TV networks, city-wide Wi-Fi

---

### 🔴 WAN — Wide Area Network

- Covers a **very large geographic area** — countries or the entire world.
- The **Internet** is the largest WAN in existence.

**Two types of WAN:**

| Type                | Description                                                           |
| ------------------- | --------------------------------------------------------------------- |
| **Distributed WAN** | Many interconnected networks, no single central location              |
| **Centralized WAN** | One main central (head office) location, branch offices connect to it |

---

### 🟣 SAN — Storage Area Network

- A special **high-speed network** used to connect servers to centralized storage devices (storage arrays, disk systems).
- Mainly used in **data centers** for storing and managing large amounts of data.
- End users don't interact with SAN directly — it works behind the scenes.

**SAN Protocols:**

| Protocol  | Full Name                                | Notes                    |
| --------- | ---------------------------------------- | ------------------------ |
| **FC**    | Fibre Channel                            | Most common, very fast   |
| **iSCSI** | Internet Small Computer System Interface | Uses IP network          |
| **FCoE**  | Fibre Channel over Ethernet              | Combines FC and Ethernet |

---

### ⚡ SD-WAN — Software-Defined Wide Area Network

- A modern WAN technology that uses **software to control and manage connections** instead of traditional hardware.
- Creates a **virtual WAN** that connects branch offices, data centers, and cloud services efficiently.

**Connection types supported:**
- MPLS (Multiprotocol Label Switching)
- Broadband internet
- LTE / 4G / 5G
- Fiber connections

**Advantages:**

| Advantage          | Description                                 |
| ------------------ | ------------------------------------------- |
| Easier Management  | Centrally managed via software              |
| Better Performance | Automatically picks the best path           |
| Lower Cost         | Uses cheaper broadband instead of only MPLS |
| Automatic Failover | Switches to backup if one link fails        |
| Improved Security  | Built-in encryption and policies            |

---

## mGRE — Multipoint Generic Routing Encapsulation

- A protocol used to create **dynamic VPN tunnels** between multiple networks — without configuring each tunnel manually.
- Used in **DMVPN (Dynamic Multipoint VPN)**.
- Allows **one device to connect to many devices automatically**.

> 💡 Traditional VPNs require manually setting up each connection. mGRE automates this — making it ideal for networks with many branch offices.

---

## [[02 - Network Architecture]]

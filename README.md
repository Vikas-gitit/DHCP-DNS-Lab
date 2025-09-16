# DHCP and DNS Lab

## 🎯 Objective

Implement a centralized **DHCP and DNS service** across two networks using Cisco Packet Tracer. The DHCP server is located in one LAN (192.168.1.0/24), while devices in the remote LAN (192.168.2.0/24) receive IP addresses via **DHCP relay (helper address)** on Router 2. Routing between LANs is handled with OSPF.

Why these services?

* DHCP automates IP address assignment, reducing manual effort and avoiding configuration errors.
* DNS translates hostnames into IP addresses, making communication simpler for users and applications.
* OSPF (Open Shortest Path First) is a dynamic routing protocol that provides fast convergence and scalability, making it suitable for multi-LAN topologies.

* This lab simulates a real-world enterprise setup where core services like DHCP and DNS are centralized, while remote networks rely on routing and relay to access them.


## 🖥️ Topology

![Topology](https://github.com/Vikas-gitit/DHCP-DNS-Lab/blob/master/Screenshot/01_Topology.png)

* **LAN 1 (192.168.1.0/24)** → PC1, PC2, DHCP/DNS Server
* **LAN 2 (192.168.2.0/24)** → PC3, PC4
* **WAN link** → 10.0.0.0/30 between R1 & R2

## ⚙️ Implementation Steps

1. **IP Addressing**

   * Assigned static IPs to routers and server.
   * PCs configured via DHCP.

2. **DHCP Server Setup**

   * DHCP Pool for `192.168.1.0/24` and `192.168.2.0/24`.
   * DNS configured to resolve hostnames.

3. **Router Configuration**

   * OSPF enabled in Area 0 on R1 & R2.
   * R2 configured with `ip helper-address 192.168.1.100` for DHCP relay.

4. **Testing & Verification**

   * `ipconfig /all` before and after DHCP request on PCs.
   * Successful ping from PC1 (LAN1) → PC3 (LAN2) and vice versa.

## 📂 Repository Structure

```
DHCP-DNS/
│
├── Configs/                     # Router configurations
│   ├── R1_Config.txt
│   └── R2_Config.txt
│
├── PacketTracer_Files/           # Packet Tracer topology files
│   └── DHCP-DNS.pkt
│
├── Screenshots/                  # Proof of DHCP, DNS, and connectivity
│   ├── 01_Topology.png
│   ├── 02_DHCP_Server_Pool.png
│   ├── 03_PC1_Before_DHCP.png
│   ├── 04_PC1_After_DHCP.png
│   ├── 05_PC4_Before_DHCP.png
│   ├── 06_PC4_After_DHCP.png
│   ├── 07_Ping_PC1_to_PC3.png
│   └── 08_Ping_PC3_to_PC1.png
│
└── README.md                     # Project overview and documentation

```

## 🚀 How to Use

1. Download and open `DHCP-DNS.pkt` in Cisco Packet Tracer.
2. Explore router configs under `/Configs`.
3. Review screenshots in `/Screenshots` to verify DHCP and connectivity tests.

## ✅ Validation

* PCs in both networks successfully obtained IP addresses from the centralized DHCP server.
* End-to-end connectivity verified with ICMP pings.
* DNS resolution tested within the LAN.

---


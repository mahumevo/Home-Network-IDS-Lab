# Home Network Monitoring & IDS Deployment Lab

## 📝 Project Overview
This project demonstrates the deployment of an open-source Intrusion Detection System (Suricata) inside a local network architecture to monitor, inspect, and analyze live traffic and potential security threats.

## 🛠️ Architecture & Tools Used
- **OS:** Ubuntu Linux (VirtualBox)
- **IDS:** Suricata 8.0.x
- **Network Scanner:** Nmap & Tcpdump
- **Target Environment:** Local Subnet (192.168.1.0/24)

## 🔍 Lab Exercises & Findings

### 1. Active Reconnaissance & Asset Fingerprinting
In this exercise, I performed an aggressive scan on a live active host on the subnet (`192.168.1.20` - Samsung Galaxy Z Fold7) to analyze open ports and service banners:
- **Command used:** `sudo nmap -A -T4 192.168.1.20`
- **Key Discovery:** Port `7019/TCP` detected in a `filtered` state, mapped to the `doceri-ctl` service (commonly used for screen mirroring/multimedia streaming tools like Samsung Smart View). 
- **Security Analysis:** The host demonstrated strong security posture with 999 closed ports and randomized MAC address protection.

### 2. Live Traffic Analysis (STUN Protocol & NAT Traversal)
While monitoring the network, Suricata captured a series of interaction logs involving an internal asset (`192.168.1.205`) communicating with an external Cloudflare server (`162.159.207.0:3478`):
- **Log Data:**
  ```text
  [1:2016149:3] ET INFO Session Traversal Utilities for NAT (STUN Binding Request) -> UDP 192.168.1.205:63591 -> 162.159.207.0:3478
  [1:2016150:3] ET INFO Session Traversal Utilities for NAT (STUN Binding Response) -> UDP 162.159.207.0:3478 -> 192.168.1.205:63591

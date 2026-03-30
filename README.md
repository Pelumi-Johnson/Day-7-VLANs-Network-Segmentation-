# Day 7 | VLANs (Network Segmentation)

## 🎯 Objective
Understand what VLANs are, why networks are segmented, and how switches can control communication between devices.

---

## 🧠 Core Idea
A switch connects devices physically.

A VLAN decides which devices are allowed to communicate logically.

Without VLANs:
- all devices share the same network space

With VLANs:
- communication is controlled and segmented

---

## 🌐 What is a VLAN
A VLAN (Virtual Local Area Network) is a logical separation of devices within the same physical switch.

Devices in different VLANs behave as if they are on completely separate networks.

![VLAN Concept](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-30%20035659.png)

---

## 🧠 Analogy
One building with multiple departments:
- HR
- IT
- Finance

Same building (switch), but different rooms (VLANs).

Devices are grouped based on function, not just physical connection.

---

## 🧪 Lab Setup
Built a simple topology using:
- 1 Switch
- 2 PCs

No router was used in this lab to highlight VLAN isolation.

![Topology](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-29%20122140.png)

---

## ⚙️ VLAN Configuration (Switch CLI)

Created two VLANs:

enable  
configure terminal  

vlan 10  
name HR  
exit  

vlan 20  
name IT  
exit  

![VLAN Creation](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-29%20122909.png)

## 🔌 Port Assignment

Assigned switch ports to VLANs:

### PC0 → VLAN 10 (HR)

interface fastEthernet 0/1  
switchport mode access  
switchport access vlan 10  
exit  

---

### PC1 → VLAN 20 (IT)

interface fastEthernet 0/2  
switchport mode access  
switchport access vlan 20  
exit 

---

## 🖥️ IP Addressing

Both devices were assigned IPs in the same range:

PC0:
192.168.1.1
255.255.255.0  

PC1:
192.168.1.2  
255.255.255.0  

![IP Configuration](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-29%20122921.png)

---

![IP Configuration](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-29%20122935.png)


---

## 📡 Connectivity Test

From PC0:

ping 192.168.1.20  

![Ping Test](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-29%20123047.png)

---

## ❌ Result
Communication failed.

---

## 🧠 Why It Failed

Even though:
- both devices are connected to the same switch  
- both devices are in the same IP range  

They are in different VLANs:

- PC0 → VLAN 10  
- PC1 → VLAN 20  

This creates logical separation.

Devices in different VLANs cannot communicate without routing.

---

## 🔍 Verification

Checked VLAN configuration using:

show vlan brief  

Expected result:
- VLAN 10 assigned to Fa0/1  
- VLAN 20 assigned to Fa0/2  

### 📸 Insert Screenshot Here
![VLAN Verification](https://github.com/Pelumi-Johnson/Day-7-VLANs-Network-Segmentation-/blob/main/Screenshot%202026-03-29%20123228.png)

---

## 🧠 Key Concepts Learned

- VLANs logically separate devices within the same switch  
- Devices in different VLANs cannot communicate directly  
- VLANs improve network organization and security  
- Port assignments determine VLAN membership  
- IP range alone does not guarantee communication  

---

## 🔁 Practical Reinforcement

- Created VLANs from scratch  
- Assigned switch ports to different VLANs  
- Configured IP addresses  
- Tested communication  
- Observed failure due to VLAN separation  
- Verified VLAN configuration  

---

## ✅ Outcome

Developed a deeper understanding of network segmentation and how VLANs control communication within a switch.

This lab introduced the foundation of network isolation, traffic control, and structured network design.

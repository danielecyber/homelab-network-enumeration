# Homelab Network Enumeration – Kali → Ubuntu Date: 2025-12-15


This repository documents a **realistic internal network enumeration exercise**
performed inside a personal HomeLab using Kali Linux as the attacker
and Ubuntu Linux as the target.

The goal is to practice **methodical reconnaissance**, command logging,
and report-style documentation exactly as done in professional penetration tests.

- Network enumeration
- Nmap scanning
- Documentation discipline

---

## Lab Environment

### Attacker
- OS: Kali Linux
- IP address: 192.168.122.25
- Interface: eth0

### Target
- OS: Ubuntu Server/Desktop
- IP address: 192.168.122.95
- Interface: enpXsY

### Network
- Type: libvirt NAT
- Gateway: 192.168.122.1
- Subnet: 192.168.122.0/24

---

## Objective

- Verify connectivity
- Discover live hosts
- Identify exposed services
- Build clean enumeration notes
- Prepare findings for future exploitation phases

---

## Step 1 – Connectivity Check

From Kali:

```bash
ping -c 4 192.168.122.95
Result:

Ping successful

No packet loss

Stable latency

This confirms basic Layer 3 connectivity.

Step 2 – Local Network Discovery
nmap -sn 192.168.122.0/24


Discovered hosts:

IP Address	Hostname
192.168.122.1	gateway
192.168.122.25	kali
192.168.122.95	ubuntu

Only expected machines are present.
No rogue devices detected.

Step 3 – ARP Table Inspection
arp -a


Observed entries:

192.168.122.1 → gateway

192.168.122.95 → ubuntu

Confirms direct Layer 2 visibility of the target.

Step 4 – TCP Port Scan (SYN Scan)
nmap -sS -Pn 192.168.122.95


Results:

Port	State	Service
22	open	ssh
Initial Analysis

Only SSH is exposed

Indicates a hardened or minimal Ubuntu installation

SSH likely default configuration

Potential next steps:

Service version detection

SSH configuration review

Credential-based attacks (only if authorized)

Brute-force testing in lab context

Notes

All commands were executed manually

Output was logged in real time using nano

No automated exploitation performed

This repository focuses on enumeration discipline, not exploitation

Next Steps (Planned)

nmap -sV -p 22

ssh-audit

User enumeration (lab only)

Expand lab with Windows target

Disclaimer

This project is for educational purposes only
and was conducted in a private HomeLab environment.

Unauthorized testing against real systems is illegal.

Author

Daniele
Cybersecurity student
HomeLab-based learning approach


---

### Cosa fai adesso (senza pensarci troppo)
1. In alto: **Name your file → `README.md`**
2. Incolla tutto
3. **Commit changes**
4. Messaggio commit:

# Network-scanner-lite

A fast, no-dependencies LAN recon tool:
Scan multiple CIDRs and/or sweep common private spaces as /24 chunks
Ping → SendARP to fetch MAC addresses
MAC filter with * wildcards
Reverse DNS and NetBIOS hostnames
OUI vendor lookup from a local oui.txt
Quick port checks (TCP connect) to hint device type
ARP-only instant listing
Add My Adapters (auto-discovers local subnets)
Wake-on-LAN (magic packet)
Export CSV
Stop button + host cap so you don’t accidentally scan the world
Row context menu: Ping, open HTTP/HTTPS, RDP, SSH, Copy IP/MAC, WOL
Works best when run as Administrator (ARP + name lookups more reliable).

Ex:
IP              MAC                Name              Vendor       OpenPorts     Status
192.168.1.10    A0:B1:C2:...      printer.local     HP Inc.      80,443        SEEN
192.168.1.25    3C:5A:B4:...      win10-pc          Dell         135,445,3389  NEW
...
Features

Multi-CIDR input: paste comma or newline separated CIDRs, e.g.

192.168.1.0/24
10.10.10.0/24, 172.16.5.0/24

Private sweeps: tick 192.168/16, 172.16/12, or 10/8 to expand into /24 blocks automatically. Use the Max hosts cap to keep scans bounded.
MAC filter: match only certain devices, e.g. A0:B1:C2:* or *D4:EE* or A0B1C2*.
Names: tries reverse DNS first; if empty, tries NetBIOS (nbtstat).
Vendors (OUI): loads from oui.txt (see below).
Ports: configurable CSV (defaults: 22,80,443,445,3389,5357,5900).
ARP table: list already-seen devices instantly (arp -a).
Adapters: auto-read your local adapters and add their CIDRs.
WOL: right-click a row → Wake-on-LAN (broadcast).
OUI Vendor Database

Create a file oui.txt beside the script. Each line should be one of:

A1-B2-C3,Vendor Name
A1:B2:C3 Vendor Name
A1B2C3 Vendor Name

Comments with # are ignored.

Example:
# Prefix,Vendor
A0-B1-C2,MyVendor Inc.
3C:5A:B4 ACME Devices
00163E Huawei Technologies Co.,Ltd

Privacy & Ethics
Only scan networks you own or have permission to test. Respect policies and law.

Tip: you can copy/paste from public OUI lists and keep only the first 6 hex + vendor.

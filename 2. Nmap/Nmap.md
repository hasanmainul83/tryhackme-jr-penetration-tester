
Nmap (Network Mapper) is a network scanning tool used to discover live hosts, identify open ports, detect services, and map a network.

## 1. Live Host Discovery

Command syntax:

```
nmap [FLAGS] TARGET
```

Important switches:

```
-sn           → Host discovery only; no port scan
-PE           → ICMP Echo Request
-PP           → ICMP Timestamp Request
-PM           → ICMP Address Mask Request
-PS           → TCP SYN ping
-PA           → TCP ACK ping
-PU           → UDP ping
-PR           → ARP discovery
-Pn           → Skip host discovery; treat hosts as online
-R            → Force reverse DNS resolution
-n            → Disable DNS resolution
```

Example:

```
nmap -sn -PR 10.10.10.0/24
```

ARP discovery works only on the local subnet.

## 2. Nmap Port States

```
open              → A service is listening on the port
closed            → No service is listening, but the port is reachable
filtered          → Nmap cannot determine whether the port is open
unfiltered        → Port is reachable, but open/closed cannot be determined
open|filtered     → Could be open or filtered
closed|filtered   → Could be closed or filtered
```

## 3. Basic Port Scans

Command syntax:

```
nmap [FLAGS] TARGET
```

Example:

```
nmap -sS -p- 10.10.10.10
```

Important switches:

```
-sT           → TCP Connect scan
-sS           → TCP SYN scan
-sU           → UDP scan
-p            → Specify port(s)
-p-           → Scan all 65,535 ports
-F            → Fast scan
--top-ports   → Scan the most common ports
-T0           → Very slow timing
-T5           → Very fast timing
--min-rate    → Minimum packet rate
--max-rate    → Maximum packet rate
-r            → Scan ports sequentially
```

## 4. Advanced Port Scans

Command syntax:

```
nmap [FLAGS] TARGET
```

Example:

```
nmap --scanflags FIN,PSH,URG 10.10.10.10
```

Important switches:

```
-sN            → Null scan; no TCP flags set
-sF            → FIN scan
-sX            → Xmas scan; FIN + PSH + URG
-sM            → Maimon scan; FIN + ACK
-sA            → ACK scan; useful for firewall filtering
-sW            → Window scan
--scanflags    → Use custom TCP flags
-S             → Spoof source IP
--spoof-mac    → Spoof source MAC address
-D             → Decoy scan
-sI            → Idle/Zombie scan
-f             → Fragment packets
-ff            → Fragment packets into smaller pieces
--source-port  → Set source port
--data-length  → Add extra random data
```

## 5. Service & OS Detection

Command syntax:

```
nmap [FLAGS] TARGET
```

Example:

```
nmap -sV -O -sC 10.10.10.10
```

Important switches:

```
-sV           → Service/version detection
-O            → OS detection
-sC           → Run default NSE scripts
--script      → Specify NSE script
-A            → Aggressive scan
--traceroute  → Trace network path
--reason      → Show reason for the result
-v            → Verbose output
-vv           → Very verbose output
-d            → Debug output
-dd           → More detailed debugging
```

## 6. Saving Results

Command syntax:

```
nmap [OUTPUT_OPTION] FILENAME TARGET
```

Example:

```
nmap -oN scan.txt 10.10.10.10
```

Important switches:

```
-oN   → Normal output
-oG   → Grepable output
-oX   → XML output
-oA   → Save Normal, Grepable, and XML formats
```


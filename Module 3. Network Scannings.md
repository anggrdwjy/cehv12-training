## Module 3. Scanning Networks
#### A. Perform Host Discovery
* Task 1. Perform Host Discovery using NMAP
  * ARP Ping Scan
    ```
    nmap -sn -PR 172.23.74.125
    ```
  * UDP Ping Scan
    ```
    nmap -sn -PU 172.23.74.125
    ```
  * ICMP ECHO Ping Scan
    ```
    nmap -sn -PE 172.23.74.125
    ```
  * ICMP Timestamp Ping Scan
    ```
    nmap -sn - PP 172.23.74.125
    ```
  * ICMP Address Mask Ping Scan
    ```
    nmap -sn -PM 172.23.74.125
    ```
  * TCP SYN Ping Scan
    ```
    nmap -sn -PS 172.23.74.125
    ```
  * TCP ACK Ping Scan
    ```
    nmap -sn -PA 172.23.74.125
    ```
  * IP Protocols Ping Scan
    ```
    nmap -sn -PO 172.23.74.125
    ```

* Task 2. Perform Host Disvovery using Angry IP Scanner
  * Download Angry IP Scanner
  * Scanning IP Range 172.23.74.1 - 172.23.74.255
  * Hostname : Specific
  * IP : Netmask
  * Prefrences Scanning : Combined UDP+TCP
  * Prefrences Display : Alive hosts (responding to pings) only

#### B. Perform Port and Services Discovery
* Task 1. Perform Port and Service Discovery using MegaPing
  * Download Tools from : https://magnetsoft.com/producs-download
  * Install megaping_setup.exe
  * Running Tools MegaPing.exe

* Task 2. Perform Port and Service Discovery using NetScanTools Pro
  * Download Tools from : https://netscantools.com/ntbasicrequestform.html
  * Install netscantools_demo.exe

* Task 3. Perform Port Scanning using sx Tools
  * Detail Documents : https://github.com/v-byte-cpu/sx
  * ARP Scan
    ```
    sx arp 172.23.74.125/24
    sx arp 172.23.74.125/24 --json | tee arp.cache
    ```
  * TCP Scan
    ```
    cat arp.cache | sx tcp --json -p 1-65535 172.23.74.125
    ```
  * UDP Scan
    ```
    cat arp.cache | sx udp --json -p 1-65535 172.23.74.125
    ```

* Task 4. Explore Various Network Scanning Techniques using NMAP
  * Download Tools : https://nmap.org/zenmap
  * Install zenmap.exe
  * TCP ports and services
    ```
    nmap -sT -v 172.23.74.125
    ```
  * TCP stealth scan or TCP half-open scan
    ```
    nmap -sS -v 172.23.74.125
    ```
  * Xmas Scan
    ```
    nmap -sX -v 172.23.74.125
    ```
  * TCP Maimon Scan
    ```
    nmap -sM -v 172.23.74.125
    ```
  * ACK Flag Probe Scan
    ```
    nmap -sA -v 172.23.74.125
    ```
  * UDP Scan
    ```
    nmap -sU -v 172.23.74.125 -> Profile : intense scan
    ```
  * Scan Options
    ```
    nmap -sN -T4 -A -v 172.23.74.125
    ```
  * IDLE/IPID Header Scan
    ```
    nmap -sI -v 172.2374.125
    ```
  * SCTP INTI Scan
    ```
    nmap -sY -v 172.2374.125
    ```
  * SCTP COOKIE ECHO Scan
    ```
    nmap -sZ -v 172.2374.125
    ```
  * Detect Service Version
    ```
    nmap -sV 172.2374.125
    ```
  * Scan Asterisk
    ```
    nmap -A 172.23.74.*
    ```
    
* Task 5. Explore Various Network Scanning Techniques using Hping3
  * ACK Scan 
    ```
    hping3 -A 172.23.74.125 -p 80 -c 5
    ```
  * SYN, ACK, RST Scan
    ```
    hpin3  -8 0-100 -S 172.23.74.125 -V
    ```
  * FIN, PUSH, URG Scan
    ```
    hping3 -F -P -U 172.23.74.125 -p 80 -c 5
    ```
  * SYN+ACK Scan
    ```
    hping3 --scan 0-100 -S 172.23.74.125
    ```
  * ICMP Scan
    ```
    hping3 -1 172.23.74.125 -p 80 -c 5
    hping3 -2 172.23.74.125 -p 80 -c 5
    ```
    
#### C. Perform OS Discovery

   | Operating System | Time to Live | TCP Window Size |
   | --- | --- | --- |
   | Linux | 64 | 5840 |
   | FreeBSD | 64 | 65535 |
   | OpenBSD | 255 | 163384 |
   | Windows | 128 | 65535 bytes to 1 Gigabyte |
   | Cisco Routers | 255 | 4128 |
   | Solaris | 255 | 8760 |
   | AIX | 255 | 16384 |

* Task 1. Identify Target System OS with Time-to-Live (TTL) and TCP Window Sizes using Wireshark
  * Download Wireshark : https://www.wireshark.org/download.html
  * Open Wireshark.exe

* Task 2. Perform OS Discovery using NMAP Script Engine (NSE)
  * Aggressive Scan
    ```
    nmap -A 172.23.74.125
    ```
  * OS Discovery Scan
    ```
    nmap -O 172.23.74.125
    ```
  * Custom Script Scan
    ```
    nmap --script smb-os-discovery.nse 172.23.74.125
    ```

* Task 3. Perform OS Discovery using Unicornscan
  * Specifies Immediate
    ```
    unicornscan 172.23.74.125 -Iv
    ```

#### D. Scan Beyond IDS and Firewall (Techniques to Evade IDS/Firewall)
* Task 1. Scan Beyond IDS/Firewall using Various Evasion Techniques
  * Split IP Packets into tiny fragment packets
    ```
    nmap -f 172.23.74.1225 
    ```
  * Source Port Manipulation
    ```
    nmap -g 89 172.23.74.125 --source-port
    ```
  * Specifies number of Maximum Transmission Unit (MTU)
    ```
    nmap -mtu 8 172.23.74.125
    ```
  * Decoy Scan and RND
    ```
    nmap -D RND:10 172.23.74.125
    ```
  * Spoof Mac Scan
    ```
    nmap -sT -Pn --spoof-mac 0 172.23.74.125
    ```

* Task 2. Create Custom Packets using Colasoft Packet Builder to Scan Beyond IDS/Firewall
  * Download Colasoft Packet Builder : https://www.colasoft.com/download/products/download_packet_builder.php
  * Unzip pktbuilder.zip
  * Select Adapter -> Choose -> Ok
  * Add Packet -> ARP Packet -> Ok
  * Select Packet -> Packets.cap -> Ok

* Task 3. Create Custom UDP and TCP Packets using Hping3 to Scan Beyond IDS/Firewall
  * Sending UDP Packets
    ```
    hping3 172.23.74.125 --udp --rand-source --data 500
    ```
  * Sending TCP Packets
    ```
    hping3 172.23.74.125 --tcp --rand-source --data 500
    ```
  * Specifies TCP SYN Packets
    ```
    hping3 -S 172.23.74.125 -p 80 -c 5
    ```
  * TCP Flooding
    ```
    hping3 172.23.74.125 --flood
    ```
  * Packet Crafting Tools
  	* NetScanTools Pro
  	* Colasoft Packet

#### E. Perform Network Scanning using Various Scanning Tools
* Task 1. Scan Target Network using Metasploit
  * Start Postgresql
    ```
    service postgresql start
    ```
  * Start MSFCONSOLE
    ```
    # msfconsole
    > db_status
    ```
    ```
    # msdb init
    # service postgresql restart
    ```
    ```
    # msfconsole
  	 > db_status
  	 > nmap -Pn -sS -A -oX Test 172.23.74.0/24
  	 > db_import Test
  	 > hosts
  	 > services
    ```
  * Portscan
    ```
    # msfconsole
    > search portscan
  	 > use auxiliary/scanner/portscan/syn -> portscan SYN
  	 > set INTERFACE eth0
  	 > set PORTS 80
  	 > set RHOSTS 172.23.74.0-254
  	 > set THREADS 50
  	 > run
    ```
    ```
    # msfconsole
    > use auxiliary/scanner/portscan/tcp -> portscan TCP
  	 > set RHOSTS 172.23.74.125
  	 > run
    ```
    ```
    # msfconsole 
  	 > use auxiliary/scanner/smb/smb_version -> SMB Version
  	 > set RHOSTS 172.23.74.0-254
  	 > set THREADS 11
  	 > run
    ```


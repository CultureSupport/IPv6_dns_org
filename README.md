Public IPv6 DNS Server List and Configuration
This document provides a comprehensive list of publicly available IPv6 Domain Name System (DNS) servers and guides you through configuring your network to use one of them, specifically Cloudflare's 1.1.1.1 service.
🌎 List of Public IPv6 DNS Servers (30+ Options)
These providers offer varying degrees of speed, security, and filtering.
Provider
Primary IPv6 Address
Secondary IPv6 Address
Type / Notes
Cloudflare
2606:4700:4700::1111
2606:4700:4700::1001
Fastest, Privacy-focused
Cloudflare (Security)
2606:4700:4700::2222
2606:4700:4700::2001
Malware Filtering
Cloudflare (Family)
2606:4700:4700::1112
2606:4700:4700::1002
Malware + Adult Content Filtering
Google
2001:4860:4860::8888
2001:4860:4860::8844
General Purpose
Quad9
2620:fe::fe
2620:fe::9
Security/Malware Blocking
Quad9 (Unsecured)
2620:fe::fe:0
2620:fe::fe:9
No Security Filtering
OpenDNS
2620:119:35::35
2620:119:53::53
General Purpose
AdGuard DNS
2a00:5a60::ad1:0ff
2a00:5a60::ad2:0ff
Ad-blocking
AdGuard (Family)
2a00:5a60::bad1:0ff
2a00:5a60::bad2:0ff
Ad-blocking + Safe Search
CleanBrowsing (Family)
2a0d:2a00:2::
2a0d:2a00:1::
Family Filter
CleanBrowsing (Security)
2a0d:2a00:2::1
2a0d:2a00:1::1
Security Filter
Verisign
2620:74:1b::1:1
2620:74:1c::2:2
General Purpose
Yandex DNS
2a02:6b8::feed:0ff
2a02:6b8:0:1::feed:0ff
General Purpose
Yandex DNS (Safe)
2a02:6b8::feed:1ff
2a02:6b8:0:1::feed:1ff
Safe Filtering
Comodo Secure DNS
2001:4f8:1:f::e
2001:4f8:1:2::e
Security Filtering
DNS.WATCH
2001:1608:10:25::1c04:b12f
2001:1608:10:25::924b:d1b1
Unfiltered, No Logging
UncensoredDNS
2001:67c:28a::
2a01:3f8:0:101::1
Unfiltered
Neustar UltraDNS
2610:a1:1018::1
2610:a1:1019::1
General Purpose
Level3/CenturyLink
2001:4208:0000:2004::1
2001:4208:0000:2004::2
General Purpose
Hurricane Electric
2001:470:20::2
2001:470:20::2
General Purpose
⚙️ Configuration Guide: Using Cloudflare DNS (1.1.1.1)
We will use Cloudflare's Primary IPv6 address for this configuration: 2606:4700:4700::1111 and Secondary: 2606:4700:4700::1001.
A. Windows 10/11 Configuration
Open Network & Internet Settings: Right-click the Start button and select Settings > Network & Internet > Change adapter options.
Access Adapter Properties: Right-click your active connection (e.g., Ethernet or Wi-Fi) and select Properties.
Select IPv6 Protocol: Scroll down and double-click Internet Protocol Version 6 (TCP/IPv6).
Enter DNS Addresses: Select the radio button "Use the following DNS server addresses" and enter the chosen IPv6 addresses:
Preferred DNS Server: 2606:4700:4700::1111
Alternate DNS Server: 2606:4700:4700::1001
Save: Click OK twice to apply the changes.
B. macOS Configuration
Open System Settings: Click the Apple menu () and select System Settings (or System Preferences).
Navigate to Network: Click on Network.
Select Adapter: Select your active connection (e.g., Wi-Fi or Ethernet) and click Details (or Advanced...).
Enter DNS Addresses: Go to the DNS tab. Click the + button under "DNS Servers" and enter the addresses one by one:
2606:4700:4700::1111
2606:4700:4700::1001
Save: Click OK or Done, then Apply to save the changes.
C. Linux (Ubuntu/Debian) Configuration
For most modern Linux distributions using NetworkManager or systemd-resolved, you can edit the network configuration file or use the GUI tool.
Using resolv.conf (Basic)
While usually overwritten, you can try adding the lines directly to /etc/resolv.conf:
# Add to the top of /etc/resolv.conf
nameserver 2606:4700:4700::1111
nameserver 2606:4700:4700::1001
Using nmcli (NetworkManager)
To set DNS on a specific connection (replace EthernetConnectionName with your active connection name):
# Set primary DNS
nmcli connection modify EthernetConnectionName ipv6.dns 2606:4700:4700::1111

# Set secondary DNS
nmcli connection modify EthernetConnectionName +ipv6.dns 2606:4700:4700::1001

# Apply changes
nmcli connection up EthernetConnectionName
Verification: After configuration, open your command line or terminal and run a DNS lookup test to ensure the IPv6 servers are being used:
# On Linux/macOS
dig @2606:4700:4700::1111 google.com
If the results show an answer, your new IPv6 DNS is working!

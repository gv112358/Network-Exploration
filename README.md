# Basic Network Exploration and Assessment using Nmap
## Basic Network Scan:
Assuming we have a network with multiple hosts on the 192.168.1.0/24 subnet, and we want to perform a basic scan:
### nmap 192.168.1.0/24
## Quick Scan without Port Details:
### nmap -sn 192.168.1.0/24
## Saving IP Addresses to a File:
### nmap -sn 192.168.1.0/24 | awk '/Nmap scan/{gsub(/[()]/,"",$NF); print $NF > "nmap_scanned_ips"}'
## Saving Scan Output to Different Formats:
### nmap -sn 192.168.1.0/24 -oG nmap_output

-oN/-oX/-oS/-oG <file>: Output scan in normal, XML, s|<rIpt kIddi3,  and Grepable format, respectively, to the given filename


## Scanning Specific Ports:
### nmap -sV -p 22,80 192.168.1.1
## Tracing packets on a single IP:
### nmap -vv -n -sn -PE -T4 --packet-trace 192.168.1.1

-vv (Increase verbosity)

-n (No DNS resolution)

-sn (No port scan)

-PE (Use ICMP echo request queries)

-T4 (prohibits the dynamic scan delay from exceeding 10 ms for TCP ports)

--packet-trace (Trace sent and received packets) 

## Recursive DNS Proxies for Stealth Scan:
### nmap --dns-servers 8.8.4.4,8.8.8.8 -sL 192.168.1.0/24
## NSE Scripts to detect WAF on a website:
### nmap -p443 --script http-waf-detect --script-args="http-waf-detect.aggro,http-waf-detect.detectBodyChanges" www.example.com
## Using Vulners NSE Script:
### nmap -Pn -sV --script=vulners 37.123.45.67

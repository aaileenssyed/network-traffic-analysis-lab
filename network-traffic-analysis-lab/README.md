# Network Traffic Analysis: DNS, TCP Handshake, and HTTPS Flow

## Objective

The goal of this lab was to analyze what happens when a user visits a website. I captured DNS, TCP, and HTTPS/TLS traffic using Wireshark and documented the flow from domain name resolution to encrypted web communication.

## Tools Used

- Windows
- Command Prompt
- Wireshark
- Web browser
- example.com

## Concepts Covered

- DNS resolution
- IP addressing
- TCP 3-way handshake
- HTTPS/TLS encryption
- Ports 53 and 443
- Basic network troubleshooting

## Lab Steps

### 1. Checked local network configuration

I used `ipconfig` to identify my local IPv4 address, default gateway, and DNS server.

Screenshot:

`/screenshots/01-ipconfig.png`

### 2. Resolved the website domain

I used `nslookup example.com` to identify the IP address returned by DNS.

Screenshot:

`/screenshots/02-nslookup.png`

### 3. Tested connectivity

I used `ping` and `tracert` to test basic connectivity and route path.

Screenshots:

`/screenshots/03-ping.png`  
`/screenshots/04-tracert.png`

### 4. Captured DNS traffic in Wireshark

I filtered for DNS traffic and identified the query and response for the website.

Screenshot:

`/screenshots/05-wireshark-dns.png`

### 5. Captured TCP handshake

I filtered for HTTPS traffic and identified the TCP 3-way handshake: SYN, SYN-ACK, and ACK.

Screenshot:

`/screenshots/06-tcp-handshake.png`

### 6. Observed HTTPS/TLS traffic

I identified TLS Client Hello, Server Hello, and encrypted application data.

## Intentional Break/Fix Scenario

To simulate a DNS issue, I manually changed the DNS server to an invalid address. After this change, domain name resolution failed.

I confirmed that the issue was DNS-related by testing direct IP connectivity and comparing it with domain-based connectivity.

After restoring DNS settings to automatic, name resolution worked again.

## Key Findings

- DNS converts domain names into IP addresses.
- TCP uses a 3-way handshake before data transfer.
- HTTPS traffic uses TLS encryption over port 443.
- Wireshark can show connection metadata even when web traffic is encrypted.
- If IP connectivity works but domain lookup fails, the issue is likely DNS-related.

## Troubleshooting Summary

Problem: Website did not load after DNS was changed manually.

Evidence:
- `nslookup example.com` failed.
- Direct IP connectivity still worked.
- DNS server was set to an invalid address.

Resolution:
- Restored DNS settings to automatic.
- Re-tested `nslookup` and confirmed successful resolution.

## Security Relevance

Understanding DNS, TCP, and HTTPS traffic is important for network troubleshooting, SOC alert triage, firewall analysis, and incident response. Many security investigations begin by identifying which systems communicated, over which ports, and whether name resolution or connection behavior appears suspicious.

## What I Learned

This lab helped me understand the full web connection process from a networking perspective. I practiced using command-line tools and Wireshark to observe DNS queries, TCP handshakes, and encrypted HTTPS communication.

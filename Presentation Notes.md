# Presentation Notes

## 1. Reconnaissance (Information Gathering)
Find information about the target before scanning.

- **Sublist3r, crt.sh:** Discover subdomains.
- **Google Dorking, social media:** Find publicly available information.
- **WhatWeb:** Identify website technologies.
- **Burp Suite:** Inspect web requests and responses.

## 2. Network Scanning — Nmap
Discover live hosts, open ports, services, and versions.

- **Nmap:** Scan ports and identify services and operating systems.
- Example: `nmap -sV <target-ip>`
- **Goal:** Identify exposed services for further investigation.

## 3. Service Enumeration
Investigate discovered services for possible weaknesses.

- **HTTP/HTTPS:** Burp Suite and web-directory discovery tools.
- **SMB:** `smbclient` and `enum4linux-ng` to investigate shares and permissions.
- **SSH:** Examine service versions and authentication settings.

## 4. Vulnerability Research and Nessus
Identify and verify potential security weaknesses.

- **Searchsploit:** Search a local database of public exploits.
- **Nessus:** Scan for known vulnerabilities and misconfigurations.
- **Key point:** Scanner findings need verification before being reported as confirmed vulnerabilities.

## 5. Exploitation and Shells
Demonstrate the impact of a verified vulnerability in an authorized lab.

- **Metasploit:** Run supported exploit modules and manage sessions.
- **Netcat:** Useful for basic network connections and shell demonstrations.
- **Reverse shell vs. bind shell:** Two different ways a command-line session can connect.
- **Staged vs. non-staged payloads:** Payloads delivered in parts versus as one complete payload.
- **Manual exploitation:** Test a vulnerability without relying entirely on an automated framework.

## 6. Password Attacks
Understand common authentication weaknesses.

- **Brute force:** Try many password candidates.
- **Credential stuffing:** Test previously exposed username/password pairs.
- **Password spraying:** Try a small number of common passwords against multiple accounts.

## 7. Buffer Overflow
Learn how memory-handling errors can affect program execution.

- **Fuzzing:** Send varied inputs to find crashes.
- **Finding the offset:** Determine where input reaches a control value.
- **Bad characters and modules:** Identify problematic bytes and suitable exploit components.
- **Shellcode:** Machine code used as a payload in some exploit demonstrations.

## 8. Vulnerable-Machine Walkthroughs
Add your practical demonstrations here:

- **Blue**
- **Academy**
- **Dev**
- **Butler**
- **Blackpearl**

For each machine, present: **Scan → Enumerate → Identify vulnerability → Validate access → Explain impact → Recommend a fix.**

## Conclusion
**Reconnaissance → Scanning → Enumeration → Vulnerability Research → Validation → Reporting**

Use these tools only on systems you own or are explicitly authorized to test.

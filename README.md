<div align="center">

<pre>
 ████████╗██████╗ ██╗   ██╗██╗  ██╗ █████╗  ██████╗██╗  ██╗███╗   ███╗███████╗
    ██╔══╝██╔══██╗╚██╗ ██╔╝██║  ██║██╔══██╗██╔════╝██║ ██╔╝████╗ ████║██╔════╝
    ██║   ██████╔╝ ╚████╔╝ ███████║███████║██║     █████╔╝ ██╔████╔██║█████╗  
    ██║   ██╔══██╗  ╚██╔╝  ██╔══██║██╔══██║██║     ██╔═██╗ ██║╚██╔╝██║██╔══╝  
    ██║   ██║  ██║   ██║   ██║  ██║██║  ██║╚██████╗██║  ██╗██║ ╚═╝ ██║███████╗
    ╚═╝   ╚═╝  ╚═╝   ╚═╝   ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝
</pre>

### 🔐 Room Write-ups · Walkthroughs · Notes · Methodology

*Documenting the grind — one room at a time.*

[![Status](https://img.shields.io/badge/STATUS-ONGOING-00FF41?style=for-the-badge&labelColor=0d1117)](.)
[![TryHackMe](https://img.shields.io/badge/TryHackMe-Profile-red?style=for-the-badge&logo=tryhackme&logoColor=white)](https://tryhackme.com)
[![GitHub](https://img.shields.io/badge/GitHub-So--hel-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/So-hel)

</div>

<br>

<pre>
╔══════════════════════════════════════════════════════════════════════════════╗
║  > initializing session...                                                   ║
║  > operator  : Sohel Shaik                                                   ║
║  > mission   : cybersecurity mastery through hands-on practice               ║
║  > status    : [ ACTIVELY ONGOING ]                                          ║
║  > approach  : complete room → document → repeat                             ║
╚══════════════════════════════════════════════════════════════════════════════╝
</pre>

<br>

---

## ◈ About This Repository

This is my personal documentation repository for **TryHackMe** — an online platform for learning cybersecurity through hands-on labs and real-world challenges.

I document every room I complete with structured write-ups, notes, and walkthroughs. This repository is **actively ongoing** and grows with every room finished — past, present, and future.

> *"Learning cybersecurity through consistent hands-on practice, documentation, and continuous improvement."*

**This repo exists to:**

- `[01]` Document every room completed — continuously updated
- `[02]` Maintain structured, referenceable notes per room
- `[03]` Build a public portfolio for VAPT & Red Teaming roles
- `[04]` Reinforce learning through disciplined write-ups

<br>

---

## ◈ Write-up Format

Each room is documented following a consistent structure:

<pre>
┌─────────────────────────────────────────────────────┐
│  01  Room Overview      →  Summary & difficulty     │
│  02  Objectives         →  Tasks & goals            │
│  03  Key Concepts       →  Theory & fundamentals    │
│  04  Enumeration        →  Recon & discovery steps  │
│  05  Tools Used         →  Tools applied & how      │
│  06  Findings           →  Results & analysis       │
│  07  Solutions          →  Walkthroughs & flags     │
│  08  Lessons Learned    →  Takeaways & reflections  │
└─────────────────────────────────────────────────────┘
</pre>

<br>

---

## ◈ Topics Covered

Rooms documented here span across these core cybersecurity domains:

<div align="center">

| 🌐 Networking | 🐧 Linux Fundamentals | 🪟 Windows Fundamentals |
|:---:|:---:|:---:|
| 🌍 Web Application Security | 🔎 Vulnerability Assessment | 💥 Penetration Testing |
| ⬆️ Privilege Escalation | 🕵️ Enumeration & Reconnaissance | 🏢 Active Directory |
| 🔬 Digital Forensics | 🖥️ Security Operations (SOC) | 🦠 Malware Analysis |
| 🔐 Cryptography | 📡 Wireless Security | 🤖 Scripting & Automation |

> ⚠️ *New topics added as rooms are completed — this list grows continuously.*

</div>

<br>

---

## ◈ Arsenal — Tools of the Trade

<pre>
┌──────────────────────┬──────────┬────────────────────────────────────────┐
│  TOOL                │ CATEGORY │  PURPOSE                               │
├──────────────────────┼──────────┼────────────────────────────────────────┤
│  nmap                │  recon   │  Network discovery & port scanning     │
│  wireshark           │  network │  Packet capture & traffic analysis     │
│  burpsuite           │  web     │  Web application security testing      │
│  metasploit          │  exploit │  Exploitation framework                │
│  gobuster            │  recon   │  Directory & DNS enumeration           │
│  hydra               │  crack   │  Online brute-force attacks            │
│  john the ripper     │  crack   │  Offline password & hash cracking      │
│  netcat              │  network │  Network connections & reverse shells  │
│  nikto               │  web     │  Web server vulnerability scanning     │
│  ffuf                │  web     │  Fast web content fuzzing              │
└──────────────────────┴──────────┴────────────────────────────────────────┘
</pre>

<br>

---

## ◈ Disclaimer

<pre>
╔══════════════════════════════════════════════════════════════════════════════╗
║                           ⚠  LEGAL NOTICE  ⚠                                ║
╠══════════════════════════════════════════════════════════════════════════════╣
║                                                                              ║
║  This repository is intended FOR EDUCATIONAL PURPOSES ONLY.                  ║
║                                                                              ║
║  All documented activities were performed within the legal, sandboxed        ║
║  training environments provided by TryHackMe.                                ║
║                                                                              ║
║  Techniques and tools described here must ONLY be used in:                   ║
║    →  Authorized penetration testing engagements                             ║
║    →  Legal CTF competitions                                                 ║
║    →  Personal lab environments you own                                      ║
║                                                                              ║
║  Unauthorized use against systems you do not own is ILLEGAL.                 ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
</pre>

<br>

---

## ◈ Author

<div align="center">

<pre>
   ██████╗  ██████╗ ██╗  ██╗███████╗██╗
  ██╔════╝ ██╔═══██╗██║  ██║██╔════╝██║
  ╚█████╗  ██║   ██║███████║█████╗  ██║
   ╚═══██╗ ██║   ██║██╔══██║██╔══╝  ██║
       ██████╔╝ ╚██████╔╝██║  ██║███████╗███████╗
       ╚═════╝   ╚═════╝ ╚═╝  ╚═╝╚══════╝╚══════╝
</pre>

**Sohel Shaik**
*Cybersecurity Enthusiast · Ethical Hacking | VAPT | Wireless Security · Founder of Cyber Beyonder*

[![GitHub](https://img.shields.io/badge/GitHub-So--hel-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/So-hel)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Sohel%20Shaik-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sohel-shaik-894288282/)
[![YouTube](https://img.shields.io/badge/YouTube-Cyber%20Beyonder-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@Hell-Kill)
[![Discord](https://img.shields.io/badge/Discord-Join%20Server-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/invite/fJ4SDB5GEs)

<br>

---

`hack the box` · `try harder` · `stay curious` · `document everything`

<br>

*⭐ If this repo helped you, a star means a lot — it keeps the motivation going!*

</div>

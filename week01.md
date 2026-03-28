Week 01 Tutorial Activities

Install Ubuntu Linux


Version: Ubuntu 24.04.4 LTS — latest Long-Term Support release, chosen for stability
Architecture: ARM64 (aarch64) — required for Apple Silicon Mac
Distribution: Server (no GUI) — lightweight, appropriate for CLI-only tasks
Access method: SSH from Mac terminal using port forwarding (Host port 2201 → Guest port 22)

I connect to the VM using:
bashssh -p 2201 sadik@127.0.0.1

<img width="650" height="462" alt="Screenshot 2026-03-28 at 12 20 11 pm" src="https://github.com/user-attachments/assets/0eccb584-72f4-47b3-8102-b4c7f28f0fee" />

Create Git repository


I created my journal repository through GitHub Classroom under the CQUniversity ICT 2025 organisation (cquict2025). 

<img width="774" height="810" alt="Screenshot 2026-03-28 at 12 22 22 pm" src="https://github.com/user-attachments/assets/013f9add-afb3-4a0e-8b79-81eafada48a9" />

Setup Git repository in Linux 

<img width="777" height="811" alt="Screenshot 2026-03-28 at 12 24 18 pm" src="https://github.com/user-attachments/assets/7523b7f7-9005-4003-8ac7-2a30d44bfe89" />

install pycipher for Python


<img width="733" height="499" alt="Screenshot 2026-03-28 at 12 30 20 pm" src="https://github.com/user-attac<img width="963" height="99" alt="Screenshot 2026-03-28 at 12 34 42 pm" src="https://github.com/user-attachments/assets/59772679-2e8d-4ee6-a265-455945eb84bb" />

Task 6: Practice Linux Command Line and Git


I practised essential Linux commands needed throughout this unit.I also practised the Git workflow.

Connect to Linux from Windows 


Task 7 in the tutorial is designed for Windows users who need PuTTY and FileZilla to connect to their Linux VM. Since I am using a Mac, these Windows-specific tools are not applicable. 
Instead, I connect directly using the built-in Mac terminal via SSH:

bash
ssh -p 2201 sadik@127.0.0.1

This achieves the same outcome as PuTTY on Windows  a secure remote login to the Ubuntu VM. For file transfers, the scp command on Mac serves the equivalent purpose of FileZilla.

<img width="963" height="99" alt="Screenshot 2026-03-28 at 12 34 42 pm" src="https://github.com/user-attachments/assets/bae48705-510e-4b31-bc47-a108abb2f592" />

<img width="517" height="122" alt="Screenshot 2026-03-28 at 12 38 29 pm" src="https://github.com/user-attachments/assets/dbe04a86-b039-4aa3-bd14-4a8efe422bdd" />
955-4f62-935d-e29c0c392c72" />

Reflection

This was primarily a setup week. The most challenging aspect was configuring SSH port forwarding on VirtualBox on Apple Silicon, as ARM64 VMs behave slightly differently from x86 systems. I had previously used Linux in COIT12201 (Electronic Crime and Digital Forensics) for forensic analysis, so basic command-line navigation was familiar. However, setting up SSH key-based authentication with GitHub was a new process that required careful attention to the GitHub documentation.


Novel Insight: ARM64 Architecture and Cryptographic Performance

During setup I noted that my Ubuntu installation runs on ARM64 (aarch64) rather than the standard x86-64 architecture used in most tutorial demonstrations. This is relevant to cryptography because ARM processors include hardware-accelerated cryptographic instructions specifically ARMv8 Cryptography Extensions which provide native AES, SHA-1, and SHA-256 acceleration at the hardware level.
This means my AES encryption benchmarks in later weeks may differ from x86 results, since operations that require software emulation on some systems are handled in dedicated silicon on ARM. This is worth noting when comparing performance results with classmates running x86 VMs, and connects directly to the unit's focus on practical cryptographic performance analysis.

Referance - https://developer.arm.com/documentation

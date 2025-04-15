# PROJECTNAME
Pivoting with Relays
## Objective

This lab focused on demonstrating how to pivot through a compromised system using Netcat relays. Simulating a real-world cyberattack, the task was to access a Windows XP machine hidden within a private network by relaying traffic through a compromised Metasploitable2 (MS2) VM from an external Kali Linux attack VM. This exercise helped reinforce the concepts of port forwarding, named pipes, and relay setups, commonly used in red teaming and post-exploitation activities.

### Skills Learned

- Understanding pivoting techniques in segmented network environments

- Setting up and managing Netcat listeners and relays

- Redirecting file contents across virtual machines securely

- Using named pipes to create forward relays in Linux

- Practicing secure information delivery across isolated networks

### Tools Used

-Netcat (ncat-portable-5.59BETA1) – Lightweight networking utility

- MS2 (Metasploitable2) – Intermediate pivot host

- Windows XP VM – Internal target system

- Kali Linux – External attacker system

- mknod, nc, ftp, and basic shell commands for relay setup and file transfers

## Steps
Ref 1: Windows XP — Netcat Listener Setup

Screenshot showing the name of the Windows XP VM and the command that redirects the contents of super_secret_file.txt into Netcat (port 8080).

Ref 2: MS2 — Netcat Forward Relay

Screenshot showing the name of the MS2 VM, the mknod pipe setup, the Netcat relay command (e.g., nc -nlvp 2222 < mypipe | nc <XP-IP> 8080) and an active connection forwarding the file to Kali.

Ref 3: Kali — Receiving the Secret Formula

Screenshot showing the command used on Kali to connect to the MS2 relay (nc <MS2-IP> 2222) and display of the secret contents from the Windows XP file.

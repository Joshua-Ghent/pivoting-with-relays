# Pivoting with Relays

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
Step 1: Redirect File into Netcat on Windows XP
On the Windows XP virtual machine, I created a text file named super_secret_file.txt containing the phrase:
“This is the secret formula! It must be protected at all costs!”
Then, I redirected the contents of this file into a Netcat listener running on port 8080.

Ref 1: Windows XP → Netcat Listener

Screenshot shows the Windows XP VM name and the command used to redirect the contents of super_secret_file.txt into a Netcat listener on port 8080.
![image](https://github.com/user-attachments/assets/d8cb2582-69e3-47b6-9efd-5b0d5b221163)


Step 2: Create Forward Relay on MS2
On the MS2 virtual machine, I created a named pipe and used Netcat to establish a forward relay. This relay listened on port 2222 and forwarded incoming data to port 8080 on the Windows XP machine. This step allowed external systems (like Kali) to indirectly access the internal Windows XP system through MS2.

Ref 2: MS2 → Netcat Forward Relay

Screenshot shows the MS2 VM name, the named pipe creation, the Netcat relay command, and an active connection forwarding the secret file from Windows XP to Kali.
![image](https://github.com/user-attachments/assets/148aea2e-e1cb-46be-8451-1a0fad629d84)


Step 3: Connect from Kali and Retrieve the Secret
On the Kali Linux virtual machine, I connected to the relay hosted on MS2. Once connected, the contents of the super_secret_file.txt were immediately displayed in the terminal, confirming that the relay and redirection setup worked as intended.

Ref 3: Kali → Received Secret Formula

Screenshot shows the command executed on Kali to connect to the MS2 relay and the successful display of the secret contents from the Windows XP file.
![image](https://github.com/user-attachments/assets/7c7cbed2-48ae-4c4a-94e1-03f3c8de149d)


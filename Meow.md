# Meow Machine Walkthrough

## Overview

This walkthrough covers the steps to compromise the "Meow" machine, part of the 'Starting Point' labs on Hack the Box, with a difficulty rating of 'Very Easy.'

## Accessing the Environment

1. **Login to Hack the Box:**
   - Access the Hack the Box portal.
   - Navigate to the Starting Point page.

2. **Choose Connection Method:**
   - Choose between a PWNBOX or an OVPN (OpenVPN) connection.
   - Use the OVPN method with Kali Linux through VirtualBox.

3. **Download and Connect:**
   - Download the VPN (.ovpn) configuration file.
   - Open a terminal and run the following command:
     ```bash
     sudo openvpn [filename].ovpn
     ```
     Replace `[filename]` with your downloaded .ovpn file.

4. **Verify Connection:**
   - Check for "Initialization Sequence Completed" in the terminal.

## Activating the Machine

1. **Refresh Browser:**
   - Refresh the browser page to view the new connection.

2. **Spawn Machine:**
   - Activate the machine by clicking the 'Spawn Machine' button.
   - Note the target's IP address.

## Completing Tasks

1. **Task 1 - What does the acronym VM stand for?**
   - Answer: Virtual Machine
      - *Virtual Machine (VM) is a virtual environment which functions as a virtual computer system with its own CPU, memory, network interface & storage, created on a physical hardware system. Hypervisor separates all the resources of machine from the hardware and provisions them properly so they can be used by the VM. Virtualization technology allows user to share a system with virtual environments.*

2. **Task 2 - What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It’s also known as a console or shell:**
   - Answer: Terminal
     - *Terminal is a text-based interface used to control a Linux computer by executing specific command with proper input.*

3. **Task 3 - What service do we use to form our VPN connection into HTB labs?**
   - Answer: OpenVPN
   - *OpenVPN is an open-source VPN protocol that makes use of virtual private network (VPN) techniques to establish safe site-to-site or point-to-point connections.*

4. **Task 4 -What is the abbreviated name for a ‘tunnel interface’ in the output of your VPN boot-up sequence output?**
   - Answer: tun
     - *TUN devices are virtual interfaces used by VPN clients to establish virtual instances of physical networking connections. TUN (network TUNnel) simulates a network layer device and operates in layer 3 carrying IP packets. TUN is used with routing*

5. **Task 5 - What tool do we use to test our connection to the target with an ICMP echo request?**
   - Answer: Ping
     - *Ping (Packet Internet Groper) is invoked using command as “ping”, which uses ICMP (Internet Control Message Protocol) to reports errors and provides information related to IP packet processing. Ping works by sending an ICMP echo request message to the provided IP address. If the computer with the destination IP address is reachable, it responds with an ICMP echo reply message.*

6. **Task 6 - What is the name of the most common tool for finding open ports on a target?**
   - Answer: Nmap
     - *Nmap (Network Mapper) is a free and open-source tool for network discovery and security auditing. It is used to discover hosts and services on a computer network by sending packets and analyzing the responses.*

7. **Task 7 - What service do we identify on port 23/tcp during our scans?**
   - Answer: Telnet
     - *TELNET (TErminaL NETwork) is a type of protocol that enables one computer to connect to local computer. It follows TCP/IP networking protocol for creating remote sessions. Telnet is not a secure protocol and is unencrypted.*

8. **Task 8 - What username is able to log into the target over telnet with a blank password?**
   - Answer: root (try admin or administrator if root fails)

9. **Task 9 - Obtain Root Flag:**
   - Use Nmap to scan the target IP.
   - Identify an open port (e.g., 23/tcp) with the Telnet service.
   - Connect using `telnet [Target_IP]` with the username "root."
   - Use `ls` to list files and `cat flag.txt` to view the "flag.txt" content.
   - Copy the flag value and submit it.

## Completion Confirmation

Upon successful submission, you will receive the message "Meow has been Pwned," indicating the successful completion of the challenge.

## Conclusion

Perform an initial Nmap scan on the target IP to identify open ports and services. In this case, port 23/tcp with the Telnet service was discovered. Connect to the target server using `telnet [target_ip]`, provide "root" as the username, and explore available files using basic commands like `ls`. Once you find the "flag.txt" file, use the `cat` command to view its content and successfully solve the machine.


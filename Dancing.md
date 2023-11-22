## Dancing Machine Challenge Walkthrough

## Overview

This walkthrough covers the steps to compromise the "Dancing" machine, part of the 'Starting Point' labs on Hack the Box, with a difficulty rating of 'Very Easy.'

1. Navigate to the Dancing Machine challenge and download the VPN (.ovpn) configuration file. Open a terminal window and run the following command:

    ```bash
    sudo openvpn [filename].ovpn
    ```

    Replace `[filename]` with the name of your downloaded `.ovpn` file for the Dancing Machine challenge.

2. Confirm the connection by checking for the "Initialization Sequence Completed" line in the terminal.

3. Refresh the page in your browser to view the new connection.

4. Activate the machine by clicking the ‘Spawn Machine’ button. Note the target IP address. Use the "ping [target_ip]" command to confirm connectivity and availability of the target server.

## Task Completion

1. Solve the following tasks:

    - **Task 1: What does the 3-letter acronym SMB stand for**
      - Answer: Server Message Block
     
   *Use nmap scan i.e. Nmap -sV [target_IP] to enumerate the available services ont the target*

    - **Task 2: What port does SMB use to operate at?**
      - Answer: 445 (Found in nmap scan)

    - **Task 3: What is the service name for port 445 that came up in our Nmap scan?**
      - Answer: microsoft-ds (Found in nmap scan)
     
   * Use the SMB Utility `SMBCLIENT` to enumerate and exploit the SMB service remotely, use command `smbclient -h` to learn the usage of smbclient and also to solve next tas*

    - **Task 4: What is the 'flag' or 'switch' that we can use with the smbclient utility to 'list' the available shares on Dancing?**
      - Answer: -L
     
   *To get all available shares on the target, use `smbclient -L [target_IP]`*

    - **Task 5: How many shares are there on Dancing?**
      - Answer: 4

    - **Task 6: What is the name of the share we are able to access in the end with a blank password?**
      - Answer: WorkShares [Using *`smbclient \\\\target_IP\\Workspaces`*]

    - **Task 7: What is the command we can use within the SMB shell to download the files we find?**
      - Answer: get

2. Exploit the SMB service using the smbclient tool available in Kali Linux:

    - Use the command `smbclient -L [target_ip]` to list all available shares.

    - Connect to the "WorkShares" share [Using *`smbclient \\\\target_IP\\Workspaces`*] without providing any password.

    - After successfully connecting use the `help` command to get all applicable commands.
  
    - List (`ls`) all available directories or files and you will find two directories.

    - Enumerate both directories to find the flag, Navigate to directories using the `cd` command and list available files using `ls`.

    - In the "James.P" directory, find the "flag.txt" file. Use the `get` command to download the file.
    - Copy the flag value and submit it in the browser to complete the challenge.

## Completion Confirmation

Upon successful submission, you will receive the message “Dancing has been Pwned,” indicating the successful completion of the challenge.

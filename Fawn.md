# Fawn Machine Challenge Walkthrough

## Overview

This walkthrough covers the steps to compromise the "Fawn" machine, part of the 'Starting Point' labs on Hack the Box, with a difficulty rating of 'Very Easy.'

## Initialization and Activation

1. Log in to the Hack the Box portal and navigate to the 'Starting Point' labs.

2. Choose your connection method and initiate the connection. If using OpenVPN, execute the following command:

    ```bash
    sudo openvpn [filename].ovpn
    ```

    Replace `[filename]` with the name of your downloaded `.ovpn` file for the Starting Point lab.

3. Confirm the connection by checking for the "Initialization Sequence Completed" line in the terminal.

4. Refresh the page in your browser to view the new connection.

5. Activate the machine by clicking the ‘Spawn Machine’ button. Note the target IP address.

## Task Completion

1. Solve the provided tasks:

    - **Task 1: What does the 3-letter acronym FTP stand for?**
      - Answer: File Transfer Protocol

    - **Task 2: Which port does the FTP service listen on usually?**
      - Answer: 21

    - **Task 3: What acronym is used for the secure version of FTP?**
      - Answer: SFTP

    - **Task 4: What is the command we can use to send an ICMP echo request to test our connection to the target?**
      - Answer: ping

   *To solve task 5 & 6 run nmap scan on the [Target_IP] i.e nmap -sV [target_ip]*
    - **Task 5 and 6: Nmap Scan**
      - From your scans, what version is FTP running on the target?
        - Identify FTP version: `vsftpd 3.0.3`
      - From your scans, what OS type is running on the target?
        - Identify OS type: Unix

    - **Task 7: What is the command we need to run in order to display the ‘ftp’ client help menu?**
      - Answer: `ftp -h`

    - **Task 8: What is username that is used over FTP when you want to log in without having an account?**
      - Answer: anonymous

    *To solve next task, we must login using FTP command using `ftp [target_IP]`*
    - **Task 9: FTP Login**
      - Command: `ftp [Target_IP]`
      - Username: anonymous
      - Password: password (default)

    - **Task 10: What is the response code we get for the FTP message ‘Login successful’?**
      - Answer: 230

    - **Task 11: There are a couple of commands we can use to list the files and directories available on the FTP server. One is dir. What is the other that is a common way to list files on a Linux system.**
      - Answer: ls

    - **Task 12: What is the command used to download the file we found on the FTP server?**
      - Answer: get

    - **Task 13: Download and Submit Flag.txt**
      - Command: `get flag.txt`

1. Open the downloaded file, copy the flag value.

2. Submit the value in the browser to solve the last task.

## Completion Confirmation

Upon successful submission, you will receive the message “Fawn has been Pwned,” indicating the successful completion of the challenge.

## Conclusion

Run an Nmap scan on [target_ip]. Port 21/tcp is open, running the FTP service. Connect to the target server using the command `ftp [target_ip]`, providing "anonymous" as the username and any random password. After login, use `ls` to check all available directories/files. Notice the "flag.txt" file, download it using the command `get flag.txt`, and successfully solve this machine.

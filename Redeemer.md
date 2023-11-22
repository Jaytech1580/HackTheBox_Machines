# Redeemer Machine Challenge Walkthrough

## Overview

This walkthrough covers the steps to compromise the "Redeemer" machine, part of the 'Starting Point' labs on Hack the Box, with a difficulty rating of 'Very Easy.'

## Redeemer Machine Challenge Walkthrough

1. Navigate to the Redeemer Machine challenge and download the VPN (.ovpn) configuration file. Open a terminal window and run the following command:

    ```bash
    sudo openvpn [filename].ovpn
    ```

    Replace `[filename]` with the name of your downloaded `.ovpn` file for the Redeemer Machine challenge.

2. Confirm the connection by checking for the "Initialization Sequence Completed" line in the terminal.

3. Refresh the page in your browser to view the new connection.

4. Activate the machine by clicking the ‘Spawn Machine’ button. Note the target IP address. Use the "ping [target_ip]" command to confirm connectivity and availability of the target server.

## Task Completion

1. Solve the following tasks:

    - **Open Ports on the Machine**
      - Run an nmap scan on the target IP using the following command:
        ```bash
        nmap -p- -sV target_ip
        ```
      - If it takes too much time, use:
        ```bash
        nmap -p- --min-rate 5000 -sV target_ip
        ```
      - Or  use:
        ```bash
        nmap -p- -T4 --open -sV target_ip
        ```

    - **Task 1: Which TCP port is open on the machine?**
      - Answer: 6379

    - **Task 2 Which service is running on the port that is open on the machine?**
      - Answer: redis
        - *Redis (REmote DIctionary Server) is an open-source advanced NoSQL key-value data store used as a database, cache, and message broker. The data is stored in a dictionary format having key-value pairs. The database is stored in the server’s RAM (in-memory) to enable fast data access. Redis also writes the contents of the database to disk at varying intervals to persist it as a backup, in case of failure.*

    - **Task 3: What type of database is Redis? Choose from the following options: (i) In-memory Database, (ii) Traditional Database**
      - Answer: In-memory Database

    - **Task 4: Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments. Redis Command-Line Utility**
      - Answer: redis-cli
      - Install with: `sudo apt install redis-tools`
      - Confirm availability and usage: `redis-cli --help`

    - **Task 5: Which flag is used with the Redis command-line utility to specify the hostname?**
      - Answer: -h
      - Connect with: `redis-cli -h target_ip`

    - **Task 6: Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?**
      - Answer: info

    - **Task 7: What is the version of the Redis server being used on the target machine?**
      - Answer: 5.0.7

    - **Task 8: Which command is used to select the desired database in Redis?**
      - Answer: select
     
    - **Task 9:How many keys are present inside the database with index 0?**
      - Answer: 4

    - **Task 10: Which command is used to obtain all the keys in a database?**
      - Answer: keys *

2. After selecting the database, list all keys using the command `keys *`.

3. Count the number of keys in the database with index 0.

4. Notice the "flag" key after executing the `key *` command. Use the command `get` to retrieve the value of the flag.

5. Copy the flag value and submit it in the browser to complete the challenge.

## Completion Confirmation

Upon successful submission, you will receive the message “Redeemer has been Pwned,” indicating the successful completion of the challenge.

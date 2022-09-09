# Service Enumeration

**Table of Contents:**

- <a href='#N'>Using Nmap</a>
- <a href='#M'>Using MsfConsole</a>
- <a href='#S'>Using Stand-Alone Tools</a>
    - <a href='#smb'>Tools for SMB</a>
    - <a href='#nc'>Netcat</a>
- <a href='#B'>Brute-forcing any Service</a>

It’s simple, just try to enumerate each service with different tools so that it can be confirmed that the information given by the tools is correct and never be dependent on one tool. Learn the Logics, Not Tools.

**Major services to focus on:**

1. SMB  (139,445)
2. FTP  (21)
3. SSH  (22)
4. HTTP  (80)
5. MySQL  (3306)

<h1 id='N'>Using Nmap</h1>

You can use Nmap scripts to enumerate services. Check out [Nmap website](https://nmap.org/nsedoc/scripts/) for the list of script names or the **scripts.db** OR **/usr/share/nmap/scripts** file in your local machine. 

```bash
nmap -p<servicePortNo> --script <scripts> --script-args <arg1>=<val1>,<arg2>=<val2> <IP>
```

**NOTE:** Nmap uses - **(hyphen)** character to seperate two words in script names.

<h1 id='M'>Using MsfConsole</h1>

You can use MsfConsole **Auxiliary** modules for service enumeration.

```bash
msfconsole> search type:auxiliary <serviceName>
```

**NOTE:** Metasploit uses **_ (underscore)** character to seperate two words in module names.

<h1 id='S'>Using Stand-Alone Tools</h1>

<h2 id='smb'>Tools for SMB</h2>

- smbmap
- smbclient
- rpcclient
- enum4linux (powerful tool)
- nmblookup

<h2 id='nc'>Netcat</h2>

You can use Netcat at any port to grab a service banner or check the behaviour of the service running on that port. Sometimes, any unknown port can run a bind shell and that won’t show any service version by Nmap so use Netcat to connect back to that port.

<h1 id='B'>Brute-Forcing any service</h1>

It is recommended to use the **HYDRA** tool for brute-forcing.

```bash
hydra -l <username> -P <passlist> <IP> <serviceName>
```

WinRM (5985/5986) service brute-forcing doesn’t supported by hydra. Use **CRACKMAPEXEC** instead.

```bash
crackmapexec winrm <IP> -d <Domain Name> -u usernames.txt -p passwords.txt
```

Brute-forcing can be done through Nmap & MsfConsole

Nmap has the naming-convention for brute-forcing scripts:  **<serviceName>-brute** 
for example: smb-brute, ssh-brute e.t.c.

MsfConsole has the naming-convention for brute-forcing modules: **<serviceName>_login**
for example: smb_login, ssh_login e.t.c.
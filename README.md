# Interest
I try to weekly work on some of the machines on HackTheBox, to include their new competitive releases. I often find myself doing the same basic actions when I first start working against a new target VM. This is a script to attempt to standardize my setup, and to kick off some of the basic scans that I would initially do. This obviously doesn't replace thoughtful system enumeration, but does kick off some basic useful activities that could be done while getting coffee ready.

# Three Main Ideas
1. Get connected - Between one machine and the next, I prefer to make sure I'm set up to pay attention to that specific target. GoTime (optionally updates Kali), verifies external connectivity (since I route Kali out of a third-party VPN), connects to the correct VPN for the given target, kicks off Wireshark, and updates my display to reflect the machine I'm working against. Having all this done the same way every time makes it easier to troubleshoot if something is failing.
2. Scan smartly - Quite a few times, I've been working with a machine and noticed hours after the fact that I've been running down a rabbit hole and missed a glaring potentially exploitable path. Trying to work through the list of available services and enumerate each in turn for potential exploitation is very helpful to make sure that I'm not spending a ton of time on something esoteric and wrong.
3. Log everything - GoTime shoves everything into a directory associated with the target machine. This makes is easy to go back and review the results and beginning picking apart the target machine with the information that was gathered.

# Future Direction
1. Refactor/Modularize - The script grew organically, and being refactored to be more modular would make extension vastly easier. I could imagine, for example, having a Web class that each of the web scans would be subclasses of, making it easier to just drop a new .py file in when working on adding a new scan.
2. Add protocols - Currently http/https and ldap are the only thing that the script processes. Checking smb, imap, pop, and snmp would be relatively straightforward to implement.
3. Other labs - I mainly focus on HTB as my pentesting practice lab, but this could be adjusted to work with other lab environments, particularly be adjusting the way VPNs are handled (or handling the VPN manually.)

Resources
* https://github.com/allenwillan/GoTime - Github repo
* https://youtu.be/_2LRRC1Thco - Video overview
* https://app.hackthebox.com/ - Virtual lab this was coded against
* https://academy.hackthebox.com/ - HTB's learning website, which inspired some of the commands and syntax
* https://nmap.org/ - Nmap has a lot of great usage information that I used to pick what I felt were ideal flags for this exercise
* https://github.com/sullo/nikto - Nikto is a good web scanner, and was included in my scan
* https://www.kali.org/tools/skipfish/ - Skipfish is another web scanner, which does a good job of scraping a website
* https://github.com/blacklanternsecurity/bbot - Bighuge BLS OSINT Tool (BBOT) was something I saw demoed at Dakotacon 2023, and decided to include. It attempts to spider and enumerate a website
* https://linux.die.net/man/1/ldapsearch - ldapsearch was something I learned about via HTB, and I included in the GoTime scans as something different from the Web scans and relatively straightforward to implement
* https://book.hacktricks.xyz/welcome/readme - Great website with a lot of quick cheat-sheets for various hacking enumeration tools

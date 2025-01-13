### [**Best tool to look for Linux local privilege escalation vectors:**](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#best-tool-to-look-for-linux-local-privilege-escalation-vectors-linpeas) [**LinPEAS**](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#system-information)[System Information](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#system-information)

- [ ]  Get **OS information**
- [ ]  Check the [**PATH**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#path), any **writable folder**?
- [ ]  Check [**env variables**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#env-info), any sensitive detail?
- [ ]  Search for [**kernel exploits**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#kernel-exploits) **using scripts** (DirtyCow?)
- [ ]  **Check** if the [**sudo version** is vulnerable](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#sudo-version)
- [ ]  [**Dmesg** signature verification failed](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#dmesg-signature-verification-failed)
- [ ]  More system enum ([date, system stats, cpu info, printers](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#more-system-enumeration))
- [ ]  [Enumerate more defenses](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#enumerate-possible-defenses)

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#drives)[Drives](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#drives)

- [ ]  **List mounted** drives
- [ ]  **Any unmounted drive?**
- [ ]  **Any creds in fstab?**

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#installed-software)[**Installed Software**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#installed-software)

- [ ]  **Check for** [**useful software**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#useful-software) **installed**
- [ ]  **Check for** [**vulnerable software**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#vulnerable-software-installed) **installed**

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#processes)[Processes](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#processes)

- [ ]  Is any **unknown software running**?
- [ ]  Is any software running with **more privileges than it should have**?
- [ ]  Search for **exploits of running processes** (especially the version running).
- [ ]  Can you **modify the binary** of any running process?
- [ ]  **Monitor processes** and check if any interesting process is running frequently.
- [ ]  Can you **read** some interesting **process memory** (where passwords could be saved)?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#scheduledcron-jobs)[Scheduled/Cron jobs?](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#scheduled-jobs)

- [ ]  Is the [**PATH**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#cron-path) being modified by some cron and you can **write** in it?
- [ ]  Any [**wildcard**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#cron-using-a-script-with-a-wildcard-wildcard-injection) in a cron job?
- [ ]  Some [**modifiable script**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#cron-script-overwriting-and-symlink) is being **executed** or is inside **modifiable folder**?
- [ ]  Have you detected that some **script** could be or are being [**executed** very **frequently**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#frequent-cron-jobs)? (every 1, 2 or 5 minutes)

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#services)[Services](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#services)

- [ ]  Any **writable .service** file?
- [ ]  Any **writable binary** executed by a **service**?
- [ ]  Any **writable folder in systemd PATH**?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#timers)[Timers](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#timers)

- [ ]  Any **writable timer**?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#sockets)[Sockets](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#sockets)

- [ ]  Any **writable .socket** file?
- [ ]  Can you **communicate with any socket**?
- [ ]  **HTTP sockets** with interesting info?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#d-bus)[D-Bus](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#d-bus)

- [ ]  Can you **communicate with any D-Bus**?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#network)[Network](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#network)

- [ ]  Enumerate the network to know where you are
- [ ]  **Open ports you couldn't access before** getting a shell inside the machine?
- [ ]  Can you **sniff traffic** using `tcpdump`?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#users)[Users](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#users)

- [ ]  Generic users/groups **enumeration**
- [ ]  Do you have a **very big UID**? Is the **machine** **vulnerable**?
- [ ]  Can you [**escalate privileges thanks to a group**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/interesting-groups-linux-pe/index.html) you belong to?
- [ ]  **Clipboard** data?
- [ ]  Password Policy?
- [ ]  Try to **use** every **known password** that you have discovered previously to login **with each**possible **user**. Try to login also without a password.

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#writable-path)[Writable PATH](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#writable-path-abuses)

- [ ]  If you have **write privileges over some folder in PATH** you may be able to escalate privileges

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#sudo-and-suid-commands)[SUDO and SUID commands](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#sudo-and-suid)

- [ ]  Can you execute **any command with sudo**? Can you use it to READ, WRITE or EXECUTE anything as root? ([**GTFOBins**](https://gtfobins.github.io/))
- [ ]  Is any **exploitable SUID binary**? ([**GTFOBins**](https://gtfobins.github.io/))
- [ ]  Are [**sudo** commands **limited** by **path**? can you **bypass** the restrictions](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#sudo-execution-bypassing-paths)?
- [ ]  [**Sudo/SUID binary without path indicated**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#sudo-command-suid-binary-without-command-path)?
- [ ]  [**SUID binary specifying path**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#suid-binary-with-command-path)? Bypass
- [ ]  [**LD_PRELOAD vuln**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#ld_preload)
- [ ]  [**Lack of .so library in SUID binary**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#suid-binary-so-injection) from a writable folder?
- [ ]  [**SUDO tokens available**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#reusing-sudo-tokens)? [**Can you create a SUDO token**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#var-run-sudo-ts-less-than-username-greater-than)?
- [ ]  Can you [**read or modify sudoers files**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#etc-sudoers-etc-sudoers-d)?
- [ ]  Can you [**modify /etc/ld.so.conf.d/**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#etc-ld-so-conf-d)?
- [ ]  [**OpenBSD DOAS**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#doas) command

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#capabilities)[Capabilities](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#capabilities)

- [ ]  Has any binary any **unexpected capability**?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#acls)[ACLs](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#acls)

- [ ]  Has any file any **unexpected ACL**?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#open-shell-sessions)[Open Shell sessions](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#open-shell-sessions)

- [ ]  **screen**
- [ ]  **tmux**

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#ssh)[SSH](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#ssh)

- [ ]  **Debian** [**OpenSSL Predictable PRNG - CVE-2008-0166**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#debian-openssl-predictable-prng-cve-2008-0166)
- [ ]  [**SSH Interesting configuration values**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#ssh-interesting-configuration-values)

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#interesting-files)[Interesting Files](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#interesting-files)

- [ ]  **Profile files** - Read sensitive data? Write to privesc?
- [ ]  **passwd/shadow files** - Read sensitive data? Write to privesc?
- [ ]  **Check commonly interesting folders** for sensitive data
- [ ]  **Weird Location/Owned files,** you may have access to or alter executable files
- [ ]  **Modified** in last mins
- [ ]  **Sqlite DB files**
- [ ]  **Hidden files**
- [ ]  **Script/Binaries in PATH**
- [ ]  **Web files** (passwords?)
- [ ]  **Backups**?
- [ ]  **Known files that contains passwords**: Use **Linpeas** and **LaZagne**
- [ ]  **Generic search**

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#writable-files)[**Writable Files**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#writable-files)

- [ ]  **Modify python library** to execute arbitrary commands?
- [ ]  Can you **modify log files**? **Logtotten** exploit
- [ ]  Can you **modify /etc/sysconfig/network-scripts/**? Centos/Redhat exploit
- [ ]  Can you [**write in ini, int.d, systemd or rc.d files**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#init-init-d-systemd-and-rc-d)?

### [](https://book.hacktricks.wiki/en/linux-hardening/linux-privilege-escalation-checklist.html#other-tricks)[**Other tricks**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#other-tricks)

- [ ]  Can you [**abuse NFS to escalate privileges**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#nfs-privilege-escalation)?
- [ ]  Do you need to [**escape from a restrictive shell**](https://book.hacktricks.wiki/en/linux-hardening/privilege-escalation/index.html#escaping-from-restricted-shells)?
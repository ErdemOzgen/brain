#scan #MitreAttack

https://attack.mitre.org/techniques/T1046/


### [TCP Port Discovery](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/pentesting-network/index.html#tcp-port-discovery)

It's very common to find that all kind of ICMP packets are being filtered. Then, all you can do to check if a host is up is **try to find open ports**. Each host has **65535 ports**, so, if you have a "big" scope you **cannot** test if **each port** of each host is open or not, that will take too much time.  
Then, what you need is a **fast port scanner** ([masscan](https://github.com/robertdavidgraham/masscan)) and a list of the **ports more used:**

bash
```bash

#Using masscan to scan top20ports of nmap in a /24 range (less than 5min) masscan -p20,21 23,25,53,80,110,111,135,139,143,443,445,993,995,1723,3306,3389,5900,8080 199.66.11.0/24
```

You could also perform this step with `nmap`, but it slower and somewhat `nmap`has problems identifying hosts up.


### [HTTP Port Discovery](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/pentesting-network/index.html#http-port-discovery)

This is just a TCP port discovery useful when you want to **focus on discovering HTTP** **services**:

bash

`masscan -p80,443,8000-8100,8443 199.66.11.0/24`


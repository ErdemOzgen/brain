### [**Trackers**](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/external-recon-methodology/index.html#trackers)

If find the **same ID of the same tracker** in 2 different pages you can suppose that **both pages** are **managed by the same team**.  
For example, if you see the same **Google Analytics ID** or the same **Adsense ID** on several pages.

There are some pages and tools that let you search by these trackers and more:

- [**Udon**](https://github.com/dhn/udon)
- [**BuiltWith**](https://builtwith.com/)
- [**Sitesleuth**](https://www.sitesleuth.io/)
- [**Publicwww**](https://publicwww.com/)
- [**SpyOnWeb**](http://spyonweb.com/)


### [**Favicon**](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/external-recon-methodology/index.html#favicon)

Did you know that we can find related domains and sub domains to our target by looking for the same favicon icon hash? This is exactly what [favihash.py](https://github.com/m4ll0k/Bug-Bounty-Toolz/blob/master/favihash.py) tool made by [@m4ll0k2](https://twitter.com/m4ll0k2) does. Here’s how to use it:

bash

`cat my_targets.txt | xargs -I %% bash -c 'echo "http://%%/favicon.ico"' > targets.txt python3 favihash.py -f https://target/favicon.ico -t targets.txt -s`

![favihash - discover domains with the same favicon icon hash](https://www.infosecmatter.com/wp-content/uploads/2020/07/favihash.jpg)

Simply said, favihash will allow us to discover domains that have the same favicon icon hash as our target.

Moreover, you can also search technologies using the favicon hash as explained in [**this blog post**](https://medium.com/@Asm0d3us/weaponizing-favicon-ico-for-bugbounties-osint-and-what-not-ace3c214e139). That means that if you know the **hash of the favicon of a vulnerable version of a web tech** you can search if in shodan and **find more vulnerable places**:

bash

`shodan search org:"Target" http.favicon.hash:116323821 --fields ip_str,port --separator " " | awk '{print $1":"$2}'`

This is how you can **calculate the favicon hash** of a web:

python

`import mmh3 import requests import codecs  def fav_hash(url):     response = requests.get(url)     favicon = codecs.encode(response.content,"base64")     fhash = mmh3.hash(favicon)     print(f"{url} : {fhash}")     return fhash`

### [**Copyright / Uniq string**](https://book.hacktricks.wiki/en/generic-methodologies-and-resources/external-recon-methodology/index.html#copyright--uniq-string)

Search inside the web pages **strings that could be shared across different webs in the same organisation**. The **copyright string** could be a good example. Then search for that string in **google**, in other **browsers** or even in **shodan**: `shodan search http.html:"Copyright string"`


So you have already:

1. Found all the **companies** inside the scope
2. Found all the **assets** belonging to the companies (and perform some vuln scan if in scope)
3. Found all the **domains** belonging to the companies
4. Found all the **subdomains** of the domains (any subdomain takeover?)
5. Found all the **IPs** (from and **not from CDNs**) inside the scope.
6. Found all the **web servers** and took a **screenshot** of them (anything weird worth a deeper look?)
7. Found all the **potential public cloud assets** belonging to the company.
8. **Emails**, **credentials leaks**, and **secret leaks** that could give you a **big win very easily**.
9. **Pentesting all the webs you found**



- [**https://github.com/yogeshojha/rengine**](https://github.com/yogeshojha/rengine)
- [**https://github.com/j3ssie/Osmedeus**](https://github.com/j3ssie/Osmedeus)
- [**https://github.com/six2dez/reconftw**](https://github.com/six2dez/reconftw)

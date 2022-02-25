# pro-ukraine

![alt text](https://github.com/vikanet/pro-ukraine/blob/main/pro-ukraine.png?raw=true)

# The invasion of Ukraine by Russian troops is a threat to the whole world safety.

My goal is to share news, tools, and ideais that one can use to make a point and step up agains this war.

# There are known Russian government controlled domains, websites, services... under tha following domains:

```
government.ru
duma.gov.ru
kremlin.ru
gov.ru
```

# Anyone can use a tool like `dig` or `nslookup` to check what servers the domains are pointing to:

```
# dig government.ru

;; ANSWER SECTION:
government.ru.          6385    IN      A       95.173.136.168
government.ru.          6385    IN      A       95.173.136.162
government.ru.          6385    IN      A       95.173.136.163
```
```
# dig duma.gov.ru

;; ANSWER SECTION:
duma.gov.ru.            1800    IN      A       95.173.130.41
duma.gov.ru.            1800    IN      A       95.173.130.42
```
```
# dig kremlin.ru

;; ANSWER SECTION:
kremlin.ru.             60      IN      A       95.173.136.71
kremlin.ru.             60      IN      A       95.173.136.72
kremlin.ru.             60      IN      A       95.173.136.70
```
```
# dig gov.ru

;; ANSWER SECTION:
gov.ru.                 1800    IN      A       95.173.128.90
```

**NOTE:** the domains might have DNS load balancers that will share the load over many server and possibly geographically assing the closest server to serve each request. Which means, the IP might not be in Russian territory but in a third-party service provider (like a CDN) somewhere else.

# It is important to ALWAYS confirm the IP address of the target really belongs to the Russian government or not:

There are many sources of this kind of information, for example https://www.nirsoft.net/countryip/ru.html. \
Just look for the IP target in the IP ranges assigned to the Russian government:

```
95.173.128.0 | 95.173.159.255 | The Federal Guard Service of the Russian Federation
```

Another great tool is https://ipgeolocation.io/.

```
"ip": 95.173.128.90
"country_name": Russia
"state_prov": Central Federal District
"city": Moscow
"latitude": 55.75501
"longitude": 37.63183
"time_zone": Europe/Moscow
"isp": The Federal Guard Service of the Russian Federation
```

# How to know what ports are open in each target IP exposed to the Internet? Port-scan!

```
nmap -sV -sC -oN scan.output 95.173.128-159.0-255
nmap -F -oN scan2.output 95.173.128-159.0-255
nmap -T5 -p 80,443 -oN scan3.output 95.173.128-159.0-255
sudo nmap -O -oN scan4.output 95.173.128-159.0-255
sudo masscan 95.173.128.0/19 -p0-443 -oX scan5.output
sudo masscan 95.173.128.0/19 -p443-1000 -oX scan6.output
```

**NOTE:** the output files of the scans abore are in this repo. Skip many hours of waiting... See also a summary file with the most relevant open ports by IP.

# What tools the Hacktivists are possibly using to sabotage Russian targets?

Hacktivists are attacking the Russian government sites trying to make them offline and to creating a huge amount of traffic in their networks. It is called Dennial-of-Server, or DoS for short. \
Pretty much anyone can run a DoS tool to make a particular IP go off line due to too many requests. See a small list of popular tools for DoS attacks:

```
Metasploit - auxiliary/dos/tcp/synflood (Flood the server with SYN packets)
Metasploit - auxiliary/dos/http/slowloris.py (Makes lots of HTTP requests and sends headers periodically to keep the connections open)
Metasploit - auxiliary/dos/http/apache_range_dos.rb (Causes high memory and CPU consumption on Apache 2.0.x through 2.0.64, and 2.2.x through 2.2.19)
Metasploit - auxiliary/dos/http/gzip_bomb_dos.rb (Generates and hosts a 10MB single-round gzip file that decompresses to 10GB)
Metasploit - auxiliary/dos/http/hashcollision_dos.rb (Can cause a web server parsing the POST parameters issued with a request into a hash table to consume hours of CPU with a single HTTP request)
Metasploit - auxiliary/dos/ssl/dtls_changecipherspec.rb (Attack against Datagram TLS in OpenSSL version 0.9.8i and earlier)
Metasploit - auxiliary/dos/ntp/ntpd_reserved_dos.rb (Created an infinite looping of NTP requests between two NTP servers)
Metasploit - auxiliary/dos/dns/bind_tsig.rb (Can crash a DNS server if it is vulnerable to CVE-2016-2776)
```

**NOTE:** DoS and DDoS are ilegal pactices in most if not all countries. Do not attempt to do it, it is a crime!

# How do the Hacktivists are able to perform Denial-of-Service attacks without being caught?

The most common way to become anonymous on the internet is by using a VPN or the Tor Network but Hacktivists oftenly use a much bigger tools: Bot Nets \
By distributing it increases the demaging power over thousands or even millions of source addresses, making it very difficul to defent against.

# What attack vector a Hacktivist uses agains a target?

Reconaissence is the first step. A simple portscan can reveal what services are behind an IP or a range of IPs. Followed by a more sofisticated fingerprinting to reveal what applications and its versions are behind each exposed (open) port.

# Help needed!

Feel free to suggest new topics, increase the lists of targets, alternative tools, etc.

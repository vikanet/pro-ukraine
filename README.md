# pro-ukraine
Lets put this guys down!

![alt text](https://github.com/vikanet/pro-ukraine/blob/main/pro-ukraine.png?raw=true)

# The invasion of Ukraine by Russian troops is a threat to the whole world safety.
My goal is to share ideais that you use to make your point and step up agains war.

# Identify russian government controlled domains, websites, services...
government.ru
duma.gov.ru
kremlin.ru
gov.ru

# Use tools like `dig` or `nslookup` to check where it is pointing to.
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
**NOTE:** Each of the domains might have DNS load balancers that will share the load over the many server and possibly geographically assing the closest server, which means each IP address should be checked before any action.

# Confirm the UP target really belongs to the Russian government.
There are many sources of this kind of information. E.g. https://www.nirsoft.net/countryip/ru.html \
Look for the IP target in the IP ranges assigned to the Russian government:

```
95.173.128.0 | 95.173.159.255 | The Federal Guard Service of the Russian Federation
```

# What tools one could use to sabotage their service?

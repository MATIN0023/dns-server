## what is dns : 



The Domain Name System (DNS) is the phonebook of the Internet. Humans access information online through domain names, like nytimes.com or espn.com. Web browsers interact through Internet Protocol (IP) addresses. DNS translates domain names to IP addresses so browsers can load Internet resources.

Each device connected to the Internet has a unique IP address which other machines use to find the device. DNS servers eliminate the need for humans to memorize IP addresses such as 192.168.1.1 (in IPv4), or more complex newer alphanumeric IP addresses such as 2400:cb00:2048:1::c629:d7a2 (in IPv6).


## How does DNS work?

The process of DNS resolution involves converting a hostname (such as www.example.com) into a computer-friendly IP address (such as 192.168.1.1). An IP address is given to each device on the Internet, and that address is necessary to find the appropriate Internet device - like a street address is used to find a particular home. When a user wants to load a webpage, a translation must occur between what a user types into their web browser (example.com) and the machine-friendly address necessary to locate the example.com webpage.

## What is a DNS A record ?
The "A" stands for "address" and this is the most fundamental type of DNS record: it indicates the IP address of a given domain. For example, if you pull the DNS records of cloudflare.com, the A record currently returns an IP address of: 104.17.210.9.


## What is a DNS AAAA record ?
DNS AAAA records match a domain name to an IPv6 address. DNS AAAA records are exactly like DNS A records, except that they store a domain's IPv6 address instead of its IPv4 address.

## what is DNS caching ? 

In the Domain Name System **(DNS), caching** is the process of temporarily storing DNS records within an operating system, browser, device, or network. DNS records translate human-readable domain names like example.com into the corresponding IP addresses like 2001:db8:3e8:2a3::b63, which can be understood by computers and devices. By storing DNS information locally, DNS caching enables domains to be translated or “resolved” **faster**, while reducing network traffic.

#### Intellare company 
needs a DNS server for its infrastructure.
For this purpose, we need to start the bind server.
Next, we will configure the bind server...

## BIND9 

First we go to install:
```BASH 
$ sudo apt install bind9 bind9-utils 
```

**The second step is for the configurations.**

### Where DNS records are written ?
```bash 
$ sudo mkdir -p /etc/bind/zones
```

And in the next section, we will configure the server's own settings in the file :

```bash
# etc/bind/named.conf.options
```

This is the configuration file for a normal mode of an option file

```bash
options {
    directory "/var/cache/bind";

    recursion yes;                        
    allow-recursion { localhost; 127.0.0.1; }; 

    allow-query { any; };                
    listen-on { any; };                  
    listen-on-v6 { any; };

    forwarders {                          
        1.1.1.1;
        8.8.8.8;
    };

    dnssec-validation auto;               
    auth-nxdomain no;                    
};
```
**recursion yes** A recursive DNS lookup is where one DNS server communicates with several other DNS servers to hunt down an IP address and return it to the client. This is in contrast to an iterative DNS query, where the client communicates directly with each DNS server involved in the lookup. 

**allow-recursion**

**allow-query**

**listen-on**

**listen-on-v6**

**forwarders**

**dnssec-validation auto**

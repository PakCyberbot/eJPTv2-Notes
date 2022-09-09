# Reconnaissance

**Table of Contents:**

- <a href='#PR'>Passive Recon</a>
- <a href='#AR'>Active Recon</a>

<h1 id='PR'>Passive Recon</h1>

You can use multiple web tech profilers in order to get accurate information about the website

- **BuiltWith** browser extension (Premium & Best)
- **Wappalyzer** browser extension
- **whatweb** Linux command-line tool

You can download the HTTrack tool to clone any website for source code analysis. Type ***sudo apt install webhttrack*** in order to install it on your Linux.

You can extract much information about the domain name and website running on that domain name using the Netcraft website.

[https://www.netcraft.com/internet-data-mining/](https://www.netcraft.com/internet-data-mining/)

There are many tools to do DNS research two of them are listed below:

**dnsrecon :** simple & nice command-line tool

[https://dnsdumpster.com/](https://dnsdumpster.com/): Great and detailed DNS info can be gathered from this website (*Active+Passive info gathering available there*)

[Wafw00f](https://github.com/EnableSecurity/wafw00f) comes pre-packaged in Kali Linux. It’s the Web Application Firewall Fingerprinting Tool. it can detect a number of firewalls.

```bash
wafw00f <URL> (-a)
```

There are many Google search filters but I am writing those which are mostly used.

**site, inurl, intitle, filetype**

You can use [Google Hacking Database](https://www.exploit-db.com/google-hacking-database) for the list of Google Dorks. You have to research for new things too, If you want to hack that thing.

https://github.com/laramies/theHarvester is used to harvest email addresses related to the target domain through Publicly available data. It’s completely passive recon. theHarvester also does subdomain enumeration in passive and active recon modes.

```bash
theHarvester -d <DomainName> -b <sources>
```

[Have I been Pwned](https://haveibeenpwned.com/) website to check if the email or phone number is pwned in the data breached or not

<h1 id='AR'>Active Recon</h1>

Here are 3 different tools to do active DNS recon.

1. **dnsenum**: automatically does zone transfer and brute-forcing after finding NS through passive recon 
2. **dig**: we have to give the NS to do a zone transfer.(*Recommended by Alexis*)
3. **fierce**: zone transfer + brute-forcing

```bash
dnsenum <DomainName>
```

```bash
dig axfr @<NameServer> <DomainName>
```

**Nmap portscanner:**

Here are some important Nmap’s options that might help you in the port scanning. Check the man page of Nmap for more detailed info.

- **-Pn** : Disable ping probe
- -**p-**: All ports scanning
- -**p80,21**: Selected ports only or ranges can be used(***80-100***)
- **-v**: verbose mode
- **-sV**: service version detection
- **-O**: OS detection
- **-sC**: Default Nmap scripts usage
- **-A**: combination of the above 3 options, sC,sV,O.
- **-T<0-5>**: Timing Template
- **-oN, -oX**: output in normal format and XML format respectively
- **—scripts:** use nmap scripts

You can check out [Nmap website](https://nmap.org/nsedoc/scripts/) for the list of script names or the **scripts.db** file in your local machine. 

There is a list of some tools that can help you to do network mapping by finding the Live Hosts on the network.

- Wireshark
- arp-scan
- ping/fping
- Nmap/zenmap(*GUI version*)
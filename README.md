# OneNote Walkthroughs
These terse 'walkthroughs' provide enough information to complete a CTF without all of the rhetoric.

- CTF Link in the description
- No visible flags
- No passwords/hashes
- No cracked hashes

### Port Scanning
Initial port scanning approach is to focus on the default top 1000 ports.
Conduct an aggressive scan against identified ports only.
```
export IP=x.x.x.x
sudo nmap -sS -T4 $IP
sudo nmap -A -px,x,x,x --script=*vuln* $IP
```
### Web server enumeration
I prefer the use of FFUF. Typical command line is:
```
ffuf -u http://$IP/FUZZ -w /usr/share/seclists/Discover/Web-Content/directory-list-2.3-small.txt -c
```
'small' contains 87,000 entries. If I feel enumeration is not finding enough data, I will substitute:
```
1377710 /usr/share/seclists/Discovery/Web-Content/combined_directories.txt
1273833 /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-big.txt
 220560 /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
  87664 /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt
  ```

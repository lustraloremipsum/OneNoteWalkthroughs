# OneNote Walkthroughs
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
sudo nmap -A -px,x,x,x $IP
```

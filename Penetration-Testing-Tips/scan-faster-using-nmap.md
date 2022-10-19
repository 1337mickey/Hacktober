# Options for scanning faster using Nmap


Here are the command line options that I use to scan large networks faster
using Nmap:


```shell
# nmap -vvv -T4 -sS -Pn -n --min-rate 250 --unique --max-retries 3 \
      --max-rtt-timeout 1000ms --min-hostgroup 256 --top-ports 580 \
      [--dns-servers 1.1.1.1,1.0.0.1,9.9.9.9,8.8.8.8,8.8.4.4] [--open] \
      -oN <filename> -oX <filename> <host1>,<host2>,...
```

Here, running as root allows Nmap to use options line `-sS`

  `-T4` sets the timing template to aggressive

  `-sS` specifies Nmap to use stealth (Half-Connect) scan

  `-Pn` disables host discovery via ping, since ping responses could be
disabled by devices

  `-n` disables DNS Resolution

  `--min-rate 250` makes Nmap send packets at the rate of 250 or more

  `--max-retries 3` makes Nmap retry a maximum of three times if no response is
received from the port being scanned

  `--max-rtt-timeout 1000ms` makes Nmap wait for a maximum of 1000 milliseconds
for a probe response

  `--unique` makes Nmap scan each address only once

  `--dns-servers 1.1.1.1,1.0.0.1,9.9.9.9,8.8.8.8,8.8.4.4` makes Nmap use the
specified DNS servers for performing Reverse DNS lookups

  `--open` shows only open ports or ports that are supposedly open

  `--min-hostgroup 256` makes Nmap scan at least 256 different hosts in
parallel depending on the network

  `--top-ports 580` makes Nmap scan top 580 ports
(See: https://nmap.org/book/performance-port-selection.html)

  `-oN <filename>` makes Nmap save the output in Nmap (Normal) format with the
specified name

  `-oX <filename>` makes Nmap save the output in XML format with the specified
name


### On a reliable network, the following options could be set:

  `--max-retries 2`

  `--max-rtt-timeout 300ms`


## Some important options

  `--resume <filename>` could be used to resume aborted scans

  `--top-ports <n>` could be used to scan the top <n> ports

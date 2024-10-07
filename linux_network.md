# Common Networking Commands on Ubuntu

| **Command**       | **Category**                 | **Description**                                                                 | **Example**                                                |
|-------------------|------------------------------|---------------------------------------------------------------------------------|------------------------------------------------------------|
| `ip`              | Network Configuration         | Manages network interfaces, IP addresses, and routes.                           | `ip addr show` (Displays IP addresses)                      |
| `ifconfig`        | Network Configuration         | Configures network interfaces (replaced by `ip`).                               | `ifconfig eth0` (Shows interface details)                   |
| `nmcli`           | Network Management            | CLI tool for managing NetworkManager.                                           | `nmcli dev status` (Lists network device status)            |
| `nmtui`           | Network Management            | Text-based interface for managing network connections.                          | Run `nmtui` to open an interactive interface.               |
| `ping`            | Network Troubleshooting       | Tests network connectivity to a host.                                           | `ping google.com`                                           |
| `traceroute`      | Network Troubleshooting       | Traces the route packets take to a network host.                                | `traceroute google.com`                                     |
| `mtr`             | Network Troubleshooting       | Combines ping and traceroute for real-time network diagnostics.                 | `mtr google.com`                                            |
| `netstat`         | Network Troubleshooting       | Displays network connections and routing tables.                                | `netstat -tuln` (Lists listening ports)                     |
| `ss`              | Network Troubleshooting       | More modern replacement for `netstat`.                                          | `ss -tuln` (Shows open ports)                               |
| `dig`             | DNS Management                | Queries DNS information about a domain. [more...](https://www.hostinger.fr/tutoriels/comment-utiliser-la-commande-dig-sous-linux)                                         | `dig google.com`<br/>`dig {url} +nostats +nocomments +nocmd`                                            |
| `nslookup`        | DNS Management                | Older tool for DNS queries.                                                     | `nslookup google.com`                                       |
| `tcpdump`         | Network Packet Analysis       | Captures network traffic for analysis.                                          | `tcpdump -i eth0`                                           |
| `iwconfig`        | Wireless Network Management   | Configures wireless network interfaces.                                         | `iwconfig wlan0`                                            |
| `iw`              | Wireless Network Management   | More modern tool for managing wireless devices.                                 | `iw dev` (Lists wireless devices)                           |
| `wpa_supplicant`  | Wireless Network Management   | Manages wireless connections for WPA/WPA2 networks.                             | Usually configured through config files and run in the background. |
| `ethtool`         | Network Interface Statistics  | Displays or changes settings of network interfaces.                             | `ethtool eth0` (Shows interface settings)                   |
| `ifstat`          | Network Interface Statistics  | Shows real-time network interface statistics.                                   | `ifstat`                                                    |
| `vnstat`          | Network Traffic Monitoring    | Monitors network traffic and usage statistics.                                  | `vnstat`                                                    |
| `scp`             | File Transfer                 | Securely copies files over SSH.                                                 | `scp file.txt user@remote:/path/to/destination`             |
| `rsync`           | File Transfer                 | Synchronizes files between systems over a network.                              | `rsync -avz file.txt user@remote:/path/to/destination`      |
| `curl`            | File Transfer                 | Transfers data to or from a server using various protocols.                     | `curl http://example.com`                                   |
| `wget`            | File Transfer                 | Downloads files from the web.                                                   | `wget http://example.com/file.tar.gz`                       |
| `ufw`             | Firewall Management           | Simplified interface for managing the firewall (`iptables`).                    | `ufw status` (Shows firewall status)                        |
| `iptables`        | Firewall Management           | Advanced firewall tool for configuring complex rules.                           | `iptables -L` (Lists firewall rules)                        |
| `nc` (Netcat)     | Network Testing               | Opens TCP/UDP connections, port scanning, and testing.                          | `nc -zv example.com 80` (Checks if port 80 is open)         |
| `telnet`          | Network Testing               | Tests network connections by connecting to remote hosts and ports.              | `telnet example.com 80`                                     |
| `iftop`           | Network Monitoring            | Displays real-time bandwidth usage for network interfaces.                      | `sudo iftop`                                                |
| `nmap`            | Network Monitoring            | Scans for hosts and services on a network.                                      | `nmap -sP 192.168.1.0/24` (Scans a subnet for live hosts)   |

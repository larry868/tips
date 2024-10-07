# Linux Tips

2. Gestion des dossiers et fichiers
3. Gestion des utilisateurs
4. ssh et clés gpg
5. Réseau
6. Cron
7. Divers

## System info

```bash
# OS's version
uname -a

# Device type
cat /proc/device-tree/model

## Hostname
hostnamectl
hostname

# disk usage
df -a

## ressource usage
top
htop

## show runing processes (with 'ps'), and there Process ID (PID)
ps aux
## killing process sending (SIGTERM) signal to the process
kill {pid}
## killing process, forced
kill -s SIGKILL  {pid}

```

## File system

```bash
# list files with their size
du -sch * .[!.]* | sort -rh

# Lookup a program file
whereis {myprog} 
# Lookup executed program file
which {myprog} 
```

## Users

```bash
# List connected users
who
echo $USER
less /etc/passwd # Exit less with q

# list configured users
getent /etc/passwd # or with 'cat'

# list users than can authenticate
awk -F'[/:]' '{if ($3 >= 1000 && $3 != 65534) print $1}' /etc/passwd

# delete a user and all his directory and files (-r)
userdel -r username
```

## Permissions

```bash
# display the current `local` permission/ownership
ls -l {directory|filename}

# make it executable
sudo chmod +x {directory|filename}

# make it readeable and writeable
sudo chmod +rw {directory|filename}

# changing the owner a,d/or the group of a directory/file
sudo chown -R [{user}]:[{group}] {directory|filename}
```

[How do I find out owner / group name for a file?](https://www.cyberciti.biz/faq/unix-linux-find-file-owner-name/)

Nota: if {directory|filename} is on remote shared drive (eg. a CIFS samba), then you need to check the samba server permissions in addition

```bash
# on the samba server (V4.13.17-Ubuntu), display connected users and SharePaths
sudo smbstatus -v
# then check permissions on the SharePaths according to the connected user
ls -la {SharePath}
```


## Network

```bash
# ip is the recommanded command, rather than the oldest ifconfig
ip addr show 
ip route show

nmcli dev status # show network device status
nmcli connection show # list available connections
netstat -tulpn # list listening ports and services
curl localhost:4001 # test access to a specific port

# Show DNS resolver
cat /etc/resolv.conf 

# Network mapping 
sudo nmap localhost # local open port
nmap -sn 192.168.0.0/24 # 24 = network mask ==> https://www.aelius.com/njh/subnet_sheet.html
nmap -Pn {WAN IP} # may take a while

# Firewall 
sudo fail2ban-client status sshd #fail2ban status
sudo iptables -L # Show blocked adresses
grep "Failed password" /var/log/auth.log # Failed SSH login Attempts
egrep "Failed|Failure" /var/log/auth.log # Failed SSH login Attempts

```

## Cron

```bash
# watch logs
grep CRON /var/log/syslog

crontab -l # list cron tasks
crontab -e # edit cron tasks

# re-start cron deamon
sudo /etc/init.d/cron start 
```

## Nano

```bash
# Getting nano back after ctrl-z
fg
```

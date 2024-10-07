# CIFS / samba 

> wording: `samba` software implements `CIFS` network protocol. [Know more...](https://unix.stackexchange.com/questions/34742/cifs-vs-samba-what-are-the-differences)


## On the server side

```bash
# display samba statut on the server side
sudo smbstatus -v

# Configured samba's users
sudo pdbedit -L -v

# start / stop samba server
sudo service smbd {start|stop|restart}
```

### Setup samba 

samba configuration file is `/etc/samba/smb.conf`

```bash
...
[global]
   client min protocol = SMB2
   client max protocol = SMB3
   map archive = no
...

[{myshare}]
   comment = shared drive
   path = /data/{myshare}
   valid users = {user1},{user2} # take care of the writting, valid users with an 's'
   directory mask = 0750 # or 0775
   create mask = 0750 # or 0775
   browseable = yes
   writeable = yes # take care of the writting, writeable with 'ea'
   read only = no
   guest ok = no
   force group = {samba_user_group}
   force create mode = 0750 # or 0775
   force directory mode = 0750 # or 0775
   public = no
...

```

Samba log files location is defined within the config file, by default they're here: /var/log/samba/. There's an overall log file and a file per client.


### Give the right permissions to shared drived

```bash
mkdir /data/{myshare}
chown :sambashare /data/{myshare}
chmod 750 /data/{myshare} # or 775
sudo chmod g+s /data/{myshare}
```

## On the client side

On the client side, a drive must be mounted and configured with fstab: `/etc/fstab`, and cifs libs must be installed.

```bash
sudo apt install cifs-utils
```

```text
...
//{IPofTheSambaServer}/{SambaServerShareName} {localDriveName} cifs _netdev,rw,uid=1000,auto,vers=3.0,credentials=/root/.sambacredentials,iocharset=utf8,file_mode=0774,dir_mode=0775 0 0
...
```

For automount, we store the credentials in a file that must be in the /root/ path: `/root/.sambacredientials`

```text
username={yourUserNameOnTheSambaServer}
password={yourPasswordOnTheSambaServer}
```

Then manually mount/unmount the drive

```bash
# mount drives configured on this file
sudo mount -a -v
# to unmount a drive
sudo umount {directory}
```

---

# References

- [Install Samba on Raspi](https://www.inpact-hardware.com/article/1013/transformez-votre-raspberry-pi-4-en-nas)
- [How to Setup a Raspberry Pi Samba Server](https://pimylifeup.com/raspberry-pi-samba/) 2022-02-14
- [How to force user grouop ownership on a samba share](https://www.thegeekdiary.com/how-to-force-user-group-ownership-of-files-on-a-samba-share/)


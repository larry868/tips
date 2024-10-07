# Linux Tips - Printing

## Setup cups

`sudo nano /etc/cups/cupsd.conf`

```bash
...
# Listen localhost:631
Port 631 # for a LAN access
...
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow @LOCAL # for a LAN access
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow @LOCAL # for a LAN access
</Location>
...
```

Start the service
```bash
sudo service cups {start|stop|restart}
sudo usermod -a -G lpadmin {user}

# admin acces in web mode
https://{local-printer-ip}:631/admin

# display printers
sudo lpinfo -v 
```

---

# References
- [How to Set Up a Print Server on Raspberry Pi Using CUPS and Ubuntu 20.04](https://medium.com/@liviu.ciulinaru/how-to-set-up-a-print-server-on-raspberry-pi-using-cups-and-ubuntu-20-04-132c83e3c2b0)
- [Command-Line Printing and Options](https://www.cups.org/doc/options.html)

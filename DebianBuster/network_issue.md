# Wired Network Connection Failed Debian Buster

Open **Network Settings**, select settings on the side of the *hostname*.

Go to **Security** --> Select **PEAP** from the dropdown box and manually configure the *hostname* and enter the *password*.

Save, close and check your connection. Hurray! if its working well. If not continue reading.


## Setting Up the Wired Configuration Manually
---

Firstly check the list of interfaces. Do `ls /sys/class/net`
Various examples would be available, continue to use "eth0" or in my case it was "ens33" and make a note of this.

### Upgrading and Network Interface Names

If you are using DHCP all you need is something like

```
auto ens33
allow-hotplug ens33
iface ens33 inet dhcp
```

**Using DHCP to automatically configure the interface**

If yu are configuring it manuall the n something like this will set the default gateway(network, broadcast and gateway are optional):

```
auto ens33
iface ens33 inet static
	address 192.168.0.1/24
	gateway 192.168.1.254
```

For more information on this visit https://wiki.debian.org/NetworkConfiguration

In terminal `ping google.com` you can see the ping which means hte network is established and now you can start using the internet.

Then `sudo service network-manager restart` to restart your networl coonnection.

---

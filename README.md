# bash-pptp-auto-reconnect
Auto start/reconnect for vpn pptp

```
Location: /usr/local/bin/vpn
Usage: vpn "ppp0" "10.0.0.1" "connection name"
```

```
/etc/crontab
* *	* * *	root	/usr/local/bin/vpn "ppp0" "10.0.0.1" "vpnconn" >/dev/null
```

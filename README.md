# bash-pptp-auto-reconnect
Auto start/reconnect for vpn pptp

## Install client
```
apt-get install pptp-linux
mcedit /etc/ppp/chap-secrets
```

## Add VPN user
```
# Secrets for authentication using CHAP
# client	server	secret		IP addresses
vpnconn		PPTP	pass		*
```

```
touch /etc/ppp/peers/vpnconn
mcedit /etc/ppp/peers/vpnconn
```

## Add VPN connection
```
pty "pptp x.x.x.x --nolaunchpppd"
name vpnconn
remotename PPTP
require-mppe-128
defaultroute
replacedefaultroute
file /etc/ppp/options.pptp
ipparam vpnconn
```

## Script location
```
Location: /usr/local/bin/vpn
```

## Usage
```
Usage: vpn "ppp0" "10.0.0.1" "vpnconn"
```

## Crontab
```
* *	* * *	root	/usr/local/bin/vpn "ppp0" "10.0.0.1" "vpnconn" >/dev/null
```

## Quick install
wget -O /usr/local/bin/vpn https://github.com/vladimirok5959/bash-pptp-auto-reconnect/releases/download/latest/vpn; chmod +x /usr/local/bin/vpn

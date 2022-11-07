# bash-pptp-auto-reconnect

Auto start/reconnect for vpn pptp

## Install client

```sh
apt-get install pptp-linux
mcedit /etc/ppp/chap-secrets
```

## Add VPN user

```sh
# Secrets for authentication using CHAP
# client	server	secret		IP addresses
vpnconn		PPTP	pass		*
```

```sh
touch /etc/ppp/peers/vpnconn
mcedit /etc/ppp/peers/vpnconn
```

## Add VPN connection

```sh
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

```sh
Location: /usr/local/bin/vpn
```

## Usage

```sh
Usage: vpn "ppp0" "10.0.0.1" "vpnconn"
```

## Crontab

```sh
* *	* * *	root	/usr/local/bin/vpn "ppp0" "10.0.0.1" "vpnconn" >/dev/null
```

## Quick install

```sh
wget -O /usr/local/bin/vpn https://github.com/vladimirok5959/bash-pptp-auto-reconnect/releases/download/latest/vpn; chmod +x /usr/local/bin/vpn
```

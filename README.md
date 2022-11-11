## x-ui-global

Project: Bring English to [x-ui](https://github.com/vaxilu/x-ui)
- README: DONE

## What is x-ui

- It's xray panel with multi-protocol, multi-user support
- You can create your own "private VPN server" with this

## Features

- System status monitoring
- Support multi-user multi-protocol, web page visualization operation
- Supported protocols: vmess, vless, trojan, shadowsocks, dokodemo-door, socks, http
- Support to configure more transmission configurations
- Traffic statistics, limit traffic, limit expiration time
- Customizable xray configuration templates
- Support https access panel (bring your own domain name + ssl certificate)
- Support one-click SSL certificate application and automatic renewal
- For more advanced configuration items, see the panel for details

## System Requirements

- CentOS 7+
- Ubuntu 16+
- Debian 8+

## Install & Upgrade

### 1. Auto install & upgrade

```shell
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

### 2. Manual install & upgrade

1. Download latest package from: https://github.com/vaxilu/x-ui/releases, generally choose the `amd64` architecture
2. Use `root` user to log in to your server then upload package to `/root/` directory

> If your server cpu architecture is not `amd64`, replace `amd64` in below command with another architecture

```shell
cd /root/
rm -rf x-ui/ /usr/local/x-ui/ /usr/bin/x-ui
tar zxvf x-ui-linux-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-linux-* x-ui/x-ui.sh
cp x-ui/x-ui.sh /usr/bin/x-ui
cp -f x-ui/x-ui.service /etc/systemd/system/
mv x-ui/ /usr/local/
systemctl daemon-reload
systemctl enable x-ui
systemctl restart x-ui
```

### 3. x-ui on Docker

> Not recommended using docker, it make ping get high

## SSL - bring HTTPS to your server - more secure

> You can using any SSL certificate content of any domain, recommended using certificate content if you don't want to apply SSL/HTTPS to your web interface, only apply to connect

#Get new SSL
```shell
apt-get update
apt-get install -y certbot
certbot certonly
```
Certificate file will be stored in /root/cert directory

## Telegram Notification Bot

> This function and tutorial are provided by [FranzKafkaYu](https://github.com/FranzKafkaYu)

Instructions for use: Set robot-related parameters in the background of the panel, including

- Telegram Bot Token
- Telegram Channel/Group ChatID
- Telegram Bot cycle runtime (crontab syntax)

Reference syntax:

- 30 * * * * * // At second 30
- ** * * * * // At every minute
- */10 * * * * // At every 10th minute.
- 30 * * * * // At minute 30
- @hourly // At minute 0
- @daily // At 00:00
- @every 8h // At minute 0 past every 8th hour

Notification content:
- Node traffic usage
- Panel login reminder
- Node expiration reminder
- Traffic warning reminder

Change time zone:

- Get correctly time in your country

```shell
ln -sf /usr/share/zoneinfo/[timezone] /etc/localtime
```
Ex:
```shell
vietnam -> ln -sf /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
```

More features are planned...
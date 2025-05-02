# Configuration for Trojan VPN environment

## Setup
1. Run [Traefik env](https://github.com/execut/env-traefik)
1. Make configs: `cp .env.example .env && cp v2ray.example.json v2ray.json && cp v2ray-client.json v2ray-client.example.json`
1. Replace email1\pass1, email2\pass2, email3\pass3 to your users in file `v2ray.json`
1. Replace email1\pass1 for client config `v2ray-client.json`
1. Replace my.domain.com to your vpn domain in `docker-compose.yml` and `.env`
1. Run v2ray on server: `docker compose up -d`
1. Run proxy on your Linux:
   1. `docker compose -f docker-compose-client.yml up -d`
   1. or via apt:
```bash
sudo aptitude install v2ray
sudo mv /etc/v2ray/config.json /etc/v2ray/config.json-old
cp v2ray-client.json /etc/v2ray/config.json
service v2ray restart
```

## Usage 
1. Test proxy via Chrome `google-chrome --proxy-server="127.0.0.1:10800"`
2. Save proxy setting in local environment permanently:
```bash
echo '
export http_proxy="127.0.0.1:10800"
export https_proxy="127.0.0.1:10800"
export no_proxy="localhost,127.0.0.1,::1"' >> /etc/environment`
```
3. Relogin
4. For Android use application https://github.com/2dust/v2flyNG/releases

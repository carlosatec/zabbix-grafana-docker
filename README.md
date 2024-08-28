# Zabbix Server with MySQL, Grafana and Traefik in a Docker Compose

## 🗒️ Describe
Images Used:
* [mysql](https://hub.docker.com/_/mysql/) - Versão 8.0
* [zabbix-server-mysql](https://hub.docker.com/r/zabbix/zabbix-server-mysql/) - Versão 7.0
* [zabbix-web-apache-mysql](https://hub.docker.com/r/zabbix/zabbix-web-apache-mysql/) - Versão 7.0
* [zabbix-web-service](https://hub.docker.com/r/zabbix/zabbix-web-service/) - Versão 7.0
* [grafana](https://hub.docker.com/r/grafana/grafana/) - Versão latest
* [traefik](https://hub.docker.com/_/traefik/) - Versão latest

## ◼️ Install
Install Docker Engine and Docker Compose by following my guide.

```shell
apt-get update
apt-get install ca-certificates curl gnupg
install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
chmod a+r /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
apt-get update
apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Clone the repository to your system and start the deployment using docker compose.

NOTE: Before, change MySQL user password and Zabbix/Grafana URL and ACME Email by editing env/db.env and .env files.

```shell
cd /opt
git clone https://github.com/alfredotavio/zabbix-grafana-docker.git
cd /opt/zabbix-grafana-docker
mkdir letsencrypt/
touch letsencrypt/acme.json
chmod 600 letsencrypt/acme.json
docker compose up -d
```

## 📂 Structure
```shell
.
├── env
│   ├── db.env
│   ├── grafana.env
│   ├── traefik.env
│   ├── zbx-rpt.env
│   ├── zbx-srv.env
│   └── zbx-web.env
├── .env
└── docker-compose.yml
```

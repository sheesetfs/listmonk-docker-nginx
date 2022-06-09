
# Listmonk Production Ready Quick Setup

Hi everyone! 👋 This repo is just an example of how you can potentially set up [listmonk](https://github.com/knadh/listmonk) in production. This setup adds SSL support to Listmonk. This repo is forked from [Yasoob's repo](https://github.com/yasoob/listmonk-setup); and, you can find his [extensive guide here](https://yasoob.me/posts/setting-up-listmonk-opensource-newsletter-mailing/), which I do recommend giving a read. There were some issues with getting the application running, hence changes were made to the config files. Below, you can find a more comprehensive guide.

## ⚙️ Installation Steps

#### 1. Clone repo (for eg. we're cloning in the home directory of the user)
	cd ~
	git clone https://github.com/smsheese/listmonk-docker-nginx.git
	cd listmonk-docker-nginx

#### 2. Set Listmonk admin username, password and database password
	nano config.toml
Edit the following lines:- <br>
line 12: admin username <br>
line 13: admin password <br>
line 20: database password (same password has to be updated on docker-compose.yml)

#### 3. Set Docker timezone and database password
	nano docker-compose.yml
Edit the following lines: <br>
line 15: set [time zone](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) <br>
line 24: set DB password (should be same as in config.toml) <br>

#### 4. Set Nginx domain name
	nano data/nginx/listmonk.conf
Set the domain name in the following lines: 3, 14, 17, 18

#### 5. Set Let's Encrypt domain and email
	nano init-letsencrypt.sh
Set domain in line 8, and email address in line 11

#### 6. Set init-letsencrypt.sh as executable
	chmod +x init-letsencrypt.sh

### 🚀 Installation & Launch

Run `/bin/bash init-letsencrypt.sh` to get the certificates set up. It will also start listmonk during the process.

 
# ELK CONFIGURATION GUIDE

<br>

### DOWNLOADING UBUNTU SERVER
1.	Download Server using provided link: https://ubuntu.com/download/server

2.	Select Option: “MANUAL SERVER INSTALLATION”

<br>

### CONFIGURE UBUNTU SERVER
 
After Reboot, Login & run following commands:

```
sudo apt update
```
```
sudo apt upgrade
```
```
Sudo apt install openssh-server
```
```
sudo systemctl restart ssh
```


<br>

### INSTALLING ELK

### 1. ElasticSearch
Run following commands:
```
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
```
```
sudo apt-get update
```
```
sudo apt-get install apt-transport-https
```
```
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
```
```
sudo apt-get update
```
```
sudo apt-get install elasticsearch
```
```
sudo service elasticsearch start
```
```
Curl -XGET http://localhost:9200
```
 <br>

### 2. Logstash

Run following commands:
```
sudo apt-get install default-jre
```
```
sudo apt-get install logstash
```
```
sudo service logstash start
```
```
sudo nano /etc/logstash/logstash.yml
```
<br>

#### Find, uncomment and edit the following:
<br>
config.reload.automatic=true<br>
config.reload.interval=3
<br>
<br>

```
sudo systemctl restart logstash.service
```
<br>

### 3. Kibana

Run following commands:
```
sudo apt-get install kibana
```
```
sudo nano /etc/kibana/kibana.yml
```
#### Find, uncomment and edit the following:
<br>
server.port: 5601
<br>elasticsearch.url: "http://localhost:9200"
<br>server.host: ”IP of the ELK ubuntu server” (this server)
<br>
<br>

```
sudo systemctl restart kibana.service
```
--------------------------------------
### ACCESSING ELK USING KIBANA DASHBOARD
<br>

#### Type in Browser (Internal Network): 
http://localhost:5601                                OR                          Using server IP:     xx.xx.xx.xx:5601
<br>
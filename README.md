 
# ELK CONFIGURATION GUIDE

# Presented by: MANAVSINGH DHINGRA
<br>
> DOWNLOADING UBUNTU SERVER
> 1.	Download Server using provided link: https://ubuntu.com/download/server

2.	Select Option: “MANUAL SERVER INSTALLATION”

<br>
CONFIGURE UBUNTU SERVER
 


➔	After Reboot, Login & run following commands:
'''
sudo apt update
'''
sudo apt upgrade
Sudo apt install openssh-server
sudo systemctl restart ssh

--------------------------------------TAKE SNAPSHOT----------------------------------------





INSTALLING ELK

1.	ElasticSearch
Run following commands:
1.	wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
2.	sudo apt-get update
3.	sudo apt-get install apt-transport-https
4.	echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
5.	sudo apt-get update
6.	sudo apt-get install elasticsearch
7.	sudo service elasticsearch start
8.	Curl -XGET http://localhost:9200
 
[ This Command is used to check if ElasticSearch is installed properly, if you do not see this content then roll back to snapshot and run above commands again ]
--------------------------------------TAKE SNAPSHOT----------------------------------------

2.	Logstash

Run following commands:
1.	sudo apt-get install default-jre
2.	sudo apt-get install logstash
3.	sudo service logstash start
4.	sudo nano /etc/logstash/logstash.yml
Find, uncomment and edit the following:
●	config.reload.automatic=true
●	config.reload.interval=3
5.	sudo systemctl restart logstash.service

--------------------------------------TAKE SNAPSHOT----------------------------------------

3.	Kibana

Run following commands:
1.	sudo apt-get install kibana
2.	sudo nano /etc/kibana/kibana.yml
Find, uncomment and edit the following:
●	server.port: 5601
(if error occurs, leave the port number to as it was when you first opened the yml file )
●	elasticsearch.url: "http://localhost:9200"
●	server.host: ”IP of the ELK ubuntu server” (this server)
3.	sudo systemctl restart kibana.service
ACCESSING ELK USING KIBANA DASHBOARD

Type in Browser (Internal Network): 

http://localhost:5601                      OR                   Using server IP:     xx.xx.xx.xx:5601

--------------------------------------TAKE SNAPSHOT----------------------------------------

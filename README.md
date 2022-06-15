# ELK (Elasticsearch + Kibana) 8.2.2 with Docker



## Setup hosting
[Go here for the installation guide](./hosting/README.md)


## Setup
```
git clone https://github.com/yasiryagi/elasticsearch-docker.git
cd elasticsearch-docker

#set up data folders
mkdir ./kibana/data
chown -R 1000:1000 ./kibana/data
chmod -R 777 ./kibana/data

mkdir ./elasticsearch/data/
chown -R 1000:1000 ./elasticsearch/data/
chmod -R 777 ./elasticsearch/data/

#Change the password
nano kibana/config/kibana.yml
docker-compose up -d
```

## Setup passwords

```
docker exec -it elasticsearch bin/elasticsearch-setup-passwords interactive
```

## Firewall

```
cp firewall/after.rules /etc/ufw/after.rules
ufw allow ssh
ufw allow https
ufw route allow proto tcp from any to any port 443/tcp
ufw enable
```

## Access 
 
> Elasticsearch: https://<elasticsearch.your.cool.url>

> Kibana: https://<kibana.your.cool.url>

> User `elastic` and password `YourPassword` 

> Note system sending data will use the anonymous user. 

## Setup  anonymous_system Role

Login into Kibana > Stack Management > Security > Roles > Create role
![Role](./pics/elasticsearch_3.PNG)


## Create a data view 

Under Kibana > Stack Management > Index Managment:


![Index](./pics/elasticsearch_1.PNG)

Under Kibana > Stack Management > Data views > create data view


- distributor-node
- storage-node
- metricbeat-8.2.3
- packetbeat-8.2.3
 
![data view](./pics/elasticsearch_2.PNG) 


## Create lead users

Kibana > Stack Management > Security > Users > Create user

![lead](./pics/elasticsearch_4.PNG)

## Create BEATS users

![lead](./pics/elasticsearch_5.PNG)


![lead](./pics/elasticsearch_6.PNG)

# ELK (Elasticsearch + Kibana) 8.2.2 with Docker



## Setup hosting
[Go here for the installation guide](./hosting/README.md)


## Setup
```
git clone https://github.com/yasiryagi/elasticsearch-docker.git
cd elasticsearch-docker

#set uo data folders
chown -R 1000:1000 ./kibana/data
chmod -R 777 ./kibana/data
chown -R 1000:1000 ./elasticsearch/data/
chmod -R 777 ./elasticsearch/data/

#Change the password
nano kibana/config/kibana.yml
docker-compose up -d
```

### Setup passwords

```
docker exec -it elasticsearch bin/elasticsearch-setup-passwords interactive
```


> Elasticsearch: https://<elasticsearch.your.cool.url>
> Kibana: https://<kibana.your.cool.url>
> User `elastic` and password 'YourPassword'


## Setup  anonymous_system Role

Login into Kibana > Stack Management > Security > Roles > Create role
![Role](./pics/elasticsearch_3.PNG)


## Create a data view 

Under Kibana > Stack Management > Index Managment should see either distributor-node, storage-node or both depend on you setup
![Role](./pics/elasticsearch_1.PNG)

Under Kibana > Stack Management > Data views create a new data view 
![Role](./pics/elasticsearch_2.PNG) 


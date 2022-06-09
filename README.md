# ELK (Elasticsearch + Logstash + Kibana) 6.4.0 with Docker

```
docker-compose up -d
```

* User `elastic` and password `123change...`
* Elasticsearch: http://localhost:9200
* Kibana: http://localhost:5601
* For logstash demo, see confs in `logstash/conf` dir
* CSV used to load data is in `logstash/csv` dir
* For elasticsearch configuration, see `elasticsearch.yml` in `elasticsearch/config` dir
* Search for test `http://localhost:9200/_search`


chown -R 1000:1000 ./kibana/data
chmod -R 777 ./kibana/data
chown -R 1000:1000 ./elasticsearch/data/
chmod -R 777 ./elasticsearch/data/





docker exec -it elasticsearch bin/elasticsearch-setup-passwords interactive

# Configure Joystream Node


```
git clone https://github.com/yasiryagi/elasticsearch-docker.git
cd elasticsearch-docker/client/
```

## Distributor Node

In joystream/distributor-node/config.yml configure the below section
```
logs:
  elastic:
    level: info
    endpoint: https://<elasticsearch.your.cool.url>
```

## Storage Node

In /etc/systemd/system/storage-node.service  add the -e flag
```
ExecStart=/root/.volta/bin/yarn storage-node server \
        -u ws://localhost:9944 \
        -w <workerId> \
        -o 3333 \
        -l /<root/joystream-storage>/log/ \
        -d /<root/joystream-storage> \
        -q http://localhost:8081/graphql \
        -p <Passowrd> \
        -k /root/keys/storage-role-key.json \
        -e https://<elasticsearch.your.cool.url> \
        -s
```
## Configure Packetbeat and Metricbeat

```
git clone https://github.com/yasiryagi/elasticsearch-docker.git
cd elasticsearch-docker/client/
```

Edit config/packetbeats/packetbeat.yml:
- name
- tags
- hosts
- username
- password


Edit config/metricbeat/metricbeat.yml:

- name
- tags
- hosts
- username
- password

# Start the containers

```
docker-compose up -d
```
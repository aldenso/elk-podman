# elk-podman

elk with podman and podman-compose

## Manual install

```
sudo dnf install -y podman podman-compose
```

```
mkdir -p /tmp/elk/data
chcon -R system_u:object_r:admin_home_t:s0 /tmp/elk
export ELK_VERSION=7.9.2
podman-compose -f podman-compose.yml build
podman-compose -f podman-compose.yml up
```

sudo systemctl stop firewalld

```
curl -XPOST -D- 'http://localhost:5601/api/saved_objects/index-pattern' \
    -H 'Content-Type: application/json' \
    -H 'kbn-version: 7.9.2' \
    -u elastic:changeme \
    -d '{"attributes":{"title":"logstash-*","timeFieldName":"@timestamp"}}'
```

```
curl -XPOST -D- 'http://localhost:5601/api/saved_objects/index-pattern' \
    -H 'Content-Type: application/json' \
    -H 'kbn-version: 7.9.2' \
    -u elastic:changeme \
    -d '{"attributes":{"title":"http-*","timeFieldName":"@timestamp"}}'
```

```
curl -XPOST -H 'Content-Type: application/json' \
http://localhost:8080 -d '{"message":"hello"}'
```

# k6-experiments

Some K6 tests and experiments and how to visualize results on Grafana with Influxdb.

## Glossary

- VU: Virtual User
- Stage: Also called "ramping" is how in the code we specify the ramping of VUs.

## Installation

More details on https://k6.io/docs/getting-started/installation.

``
docker network create k6-experiments
docker-compose up -d
``

### Grafana access

Access http://localhost:3000:
 
 - User: admin
 - Pass: admin
 
### Influxdb access

Access http://localhost:8086:

To list databases:

```
curl -G "http://localhost:8086/query?pretty=true" --data-urlencode "db=glances" --data-urlencode "q=SHOW DATABASES"
```

To create a new database:

```
curl -XPOST "http://localhost:8086/query" --data-urlencode "q=CREATE DATABASE my_db"
```

### Install k6 Grafana Plugin 

Import k6 plugin (https://grafana.com/grafana/dashboards/2587) in the Grafana panel to convert influxDb data to Grafana.

"+ -> Import" and type the ID `2587`.

## Running test

```
k6 run tests/script.js
k6 run tests/single-request.js
```

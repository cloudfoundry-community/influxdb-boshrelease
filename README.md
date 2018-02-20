# InfluxDB Bosh release

Deploy InfluxDB using Bosh.

## How to deploy

### dev release

Assuming you have a working [bosh-lite](https://bosh.io/docs/bosh-lite):

```
git clone https://github.com/cloudfoundry-community/influxdb-boshrelease.git
cd influxdb-boshrelease
bosh -e vbox -d influxdb manifests/influxdb.yml -o manifests/dev.yml
```

## Features
- defining multiple databases
- defining multiple retention policies
- defining multiple users
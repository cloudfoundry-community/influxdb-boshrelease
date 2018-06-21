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
- defining multiple users and authorizations (read, read/write and admin)

## Notes
- A builtin InfluxDB administration user `__influxdb_admin` is created for the purpose of managing databases and users. The password for this user is stored in a `root`-readable file in `/var/vcap/store`. This user should not be used for any other purpose.
- Creating additional admin users is supported but discouraged, as they could be used to delete/alter the `__influxdb_admin` user, thereby causing this release to stop working.
- Deleting users, retention policies or databases from the manifest *does not delete them from InfluxDB*
- Renaming users, retention policies or databases in the manifest is unsupported and will not work as expected (new users/RPs/databases are going to be created alongside the old ones)

## Roadmap
- Automatically rotate the `__influxdb_admin` during every deploy
- Prevent remote access using `__influxdb_admin`

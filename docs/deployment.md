
# Deployment

Currently, it's planed to deploy the application to an traditionally
virtualized server in a public datacenter.

## Folder structure

`/data/docker/` is the common root directory in which
all data is written. Under that are different folders for the container
and finally folders of the attached mounts into the docker container.

| path                        | description                            |
|-----------------------------|----------------------------------------|
| studentenportal/            | Uploaded files                         |
| mail-exchange/              | Config files mail exchange             |
| postgres/                   | Config and Data file, postgres db      |

## Docker containers

| container       | Version | description                              |
|-----------------|---------|------------------------------------------|
| studentenportal | latest  | Application server with django framework |
| postgres        | 9.3     | PostgresQL dabase                        |
| mail-exchange   | latest  | exim4 mail-exchange for auto-gen-email   |

## Networks

Both networks are internal. This option shields from compromise of the
host machine. A compromised host machine does not allow access to the
hidden applications behind it.

### database-net

Isolates the postgres database. Only studentenportal container has
logical access to the internal network.

### proxy-net

Isolates the application server from the internet. Only the proxy
container has logical access to the internal network. Additionally, it
allows the proxy to function as a WAF.
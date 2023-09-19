# Besu peers through a proxy.
Poc to join with other besu peers through a proxy; this way, besu nodes can be placed behind a DMZ without direct internet access. 

## Requirements
- docker

## Steps
- `docker-compose up -p poc -d`
- wait until all services are up and running
- you will notice that besu nodes are not generating blocks, that's because envoys proxies can't see each other because they are in different networks
- `docker network connect poc-network-a poc-envoy-b-1`
- `docker network connect poc-network-b poc-envoy-a-1`
- you must restart envoy containers to refresh network changes in the previous step.
- wait a few seconds, and you will see how besu connects with its peers and starts to generate blocks.


## Notes

This is not intened to be deployed on a production environment, you must be aware that you will need to generate new keys for besu nodes, and the proxy configuration can be different depending of the environment and the topology.

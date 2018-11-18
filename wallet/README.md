# Lokid

## Start Lokid

```bash
docker-compose up
```

## Starting the wallet

Connect to the lokid docker container:

```bash
docker exec -ti 3eb042ac8c3f /bin/bash
./loki-wallet-cli --daemon-address 127.0.0.1:18081
```

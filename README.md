## Bitcoin three-node private network in regtest mode

- Node Pool
  - RPC Port 16001, Username: user, Password: pass
- Node Bob
  - RPC Port 16002, Username: user, Password: pass
- Node Alice
  - RPC Port 16003, Username: user, Password: pass

### Addresses

- Pool:  bcrt1qfrxps3h2jrj8gxs76l7tj8628flt48kdm8njr0
- Bob:   bcrt1qm9xg8mmd8cenklwa7zg8vcn0vygypaecewjp4x
- Alice: bcrt1qms5spn5rzcsgehv9h7pz9wv3rp9j5rd8l5d2hc

### To run this image with internal ports exposed at host:

```bash
docker run -it -d -p 16001:16001 -p 16002:16002 -p 16003:16003 coinfoundry/bitcoin-private-testnet
```

### Generating blocks:

```bash
docker exec -i -t <container_id> /usr/bin/bitcoin-cli -rpcport=16001 -rpcuser=user -rpcpassword=pass -generate 1
```

### Example RPC against Node-Pool:

```bash
curl --user user:pass --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getnetworkinfo", "params": [] }' -H 'content-type: application/json;' http://127.0.0.1:16001/
```

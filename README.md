Aptos validator node

Official documents:
https://aptos.dev/nodes/ait/node-requirements/
Checking the node
https://node.aptos.zvalid.com/

## Hardware requirements:
#### For running an aptos node on incentivized testnet we recommend the following:
- CPU: 4 cores (Intel Xeon Skylake or newer)
- Memory: 8GiB RAM
- Storage: 300GB (You have the option to start with a smaller size and adjust based upon demands)


Option 1 (automatic)
Use script below for a quick installation

wget -qO aptos_validator.sh https://raw.githubusercontent.com/kj89/testnet_manuals/main/aptos/testnet/aptos_validator.sh && chmod +x aptos_validato

### Restart docker container
```
docker restart testnet-validator-1

# Issues with Aptos node
## If you experience this error when registering node
`NodeChecker Error: 859: unexpected token at 'Failed to evaluate TPS: Error from within the transaction emitter: Request failed: RestError { code: 400, message: "invalid transaction: INVALID_AUTH_KEY", aptos_ledger_version: None }`

![image](https://user-images.githubusercontent.com/50621007/176991421-71492723-d13f-4e13-b931-8fc93a8d4cc2.png)

Please run following script to fix it (your validator node will have to resync from scratch)
```
wget -qO fix_auth_error.sh https://raw.githubusercontent.com/kj89/testnet_manuals/main/aptos/testnet/fix_auth_error.sh && chmod +x fix_auth_error.sh && ./fix_auth_error.sh
```
>PS: if you run a full node, don't forget to update the waypoint.txt and genesis.blob files there too.
## To change default API port from 80 to 8080
```
cd ~/$WORKSPACE
wget -qO docker-compose.yaml https://raw.githubusercontent.com/kj89/testnet_manuals/main/aptos/testnet/docker-compose.yaml
docker compose down
docker compose up -d
```

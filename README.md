[<img src='assets\Warden-Banner.png' alt='banner' width= '99.9%'>]()

<font size = 7><center><b><u>About Warden Protocol</u></b></center></font>

* ### **[Warden Protocol](https://wardenprotocol.org/)** is a modular L1 blockchain for omnichain applications, "OApps". Our mission is to empower developers to simply launch secure OApps by giving them modular infrastructure for security, interoperability and chain abstraction.

* ### Warden Protocol is a high-throughput, low-latency, instant-finality blockchain platform for OApps developers. In monolithic blockchain architectures, all security components of an application are tightly integrated into a single, centralized unit.

<div align="center">
  <a href="https://wardenprotocol.org/"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/85aaef48-7ea4-4857-b339-985645c6850c" alt="Website" width="16%"></a>
  <a href="https://github.com/warden-protocol/wardenprotocol"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/229ec400-72ff-48ee-ac18-7bdb1f5e221a" alt="Github" width="16%"></a>
  <a href="https://twitter.com/wardenprotocol"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/3978b7fc-d575-44a6-8d41-327c14c8ba31" alt="Twitter" width="16%"></a>
  <a href="https://discord.com/invite/wardenprotocol"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/944a0b87-548d-4109-ad0c-def572d307cb" alt="Discord" width="16%"></a>
  <a href="https://wardenprotocol.org/blog"><img src="https://github.com/bartosian/celestia-tools/assets/20209819/ac52729b-64d7-44d1-9a66-1e0d159848f6" alt="Blog" width="16.2%"></a>
</div>

- [Hardware requirements](#hardware-requirements)
- [TrustedPoint Services](#trustedpoint-services)
- [Installation guide](#installation-guide)
  - [1. Install required packages](#1-install-required-packages)
  - [2. Install Go](#2-install-go)
  - [3. Build `wardend` binary](#3-build-wardend-binary)
  - [4. Set up variables](#4-set-up-variables)
  - [5. Initialize the node](#5-initialize-the-node)
  - [6. Download genesis.json](#6-download-genesisjson)
  - [7. Add seeds and peers to the config.toml](#7-add-seeds-and-peers-to-the-configtoml)
  - [8. Change ports (Optional)](#8-change-ports-optional)
  - [9. Configure prunning to save storage (Optional)](#9-configure-prunning-to-save-storage-optional)
  - [10. Set min gas price](#10-set-min-gas-price)
  - [11. Enable indexer (Optional)](#11-enable-indexer-optional)
  - [12. Create a service file](#12-create-a-service-file)
  - [13. Start the node](#13-start-the-node)
  - [14. Create a wallet for your validator](#14-create-a-wallet-for-your-validator)
  - [15. Request tokens from the faucet](#15-request-tokens-from-the-faucet)
  - [16. Check wallet balance](#16-check-wallet-balance)
  - [18. Create JSON file](#18-create-json-file)
  - [19. Make sure everything is correct](#19-make-sure-everything-is-correct)
  - [19. Create a validator](#19-create-a-validator)
- [State sync](#state-sync)
  - [1. Stop the node](#1-stop-the-node)
  - [2. Backup priv\_validator\_state.json](#2-backup-priv_validator_statejson)
  - [3. Reset DB](#3-reset-db)
  - [4. Setup required variables (One command)](#4-setup-required-variables-one-command)
  - [4. Move priv\_validator\_state.json back](#4-move-priv_validator_statejson-back)
  - [5. Start the node](#5-start-the-node)
  - [6. Check the synchronization status](#6-check-the-synchronization-status)
  - [7. Disable state sync](#7-disable-state-sync)
- [Download fresh addrbook.json](#download-fresh-addrbookjson)
  - [1. Stop the node and use `wget` to download the file](#1-stop-the-node-and-use-wget-to-download-the-file)
  - [2. Restart the node](#2-restart-the-node)
  - [3. Check the synchronization status](#3-check-the-synchronization-status)
- [Add fresh persistent peers](#add-fresh-persistent-peers)
  - [1. Extract persistent\_peers from our endpoint](#1-extract-persistent_peers-from-our-endpoint)
  - [2. Restart the node](#2-restart-the-node-1)
  - [3. Check the synchronization status](#3-check-the-synchronization-status-1)
- [Download Snapshot](#download-snapshot)
  - [1. Download latest snapshot from our endpoint](#1-download-latest-snapshot-from-our-endpoint)
  - [2. Stop the node](#2-stop-the-node)
  - [3. Backup priv\_validator\_state.json](#3-backup-priv_validator_statejson)
  - [4. Reset DB](#4-reset-db)
  - [5. Extract files fromt the arvhive](#5-extract-files-fromt-the-arvhive)
  - [6. Move priv\_validator\_state.json back](#6-move-priv_validator_statejson-back)
  - [7. Restart the node](#7-restart-the-node)
  - [8. Check the synchronization status](#8-check-the-synchronization-status)
- [Useful commands](#useful-commands)
  - [Check node status](#check-node-status)
  - [Query your validator](#query-your-validator)
  - [Query missed blocks counter \& jail details of your validator](#query-missed-blocks-counter--jail-details-of-your-validator)
  - [Unjail your validator](#unjail-your-validator)
  - [Delegate tokens to your validator](#delegate-tokens-to-your-validator)
  - [Get your p2p peer address](#get-your-p2p-peer-address)
  - [Edit your validator](#edit-your-validator)
  - [Send tokens between wallets](#send-tokens-between-wallets)
  - [Query your wallet balance](#query-your-wallet-balance)
  - [Monitor server load](#monitor-server-load)
  - [Query active validators](#query-active-validators)
  - [Query inactive validators](#query-inactive-validators)
  - [Check logs of the node](#check-logs-of-the-node)
  - [Restart the node](#restart-the-node)
  - [Stop the node](#stop-the-node)
  - [Upgrade the node](#upgrade-the-node)
  - [Delete the node from the server](#delete-the-node-from-the-server)
  - [Example gRPC usage](#example-grpc-usage)
  - [Example REST API query](#example-rest-api-query)
## Hardware requirements
```py
- Memory: 8 GB RAM
- CPU: 4 cores
- Disk: 200 GB NVME
- Bandwidth: 1 Gbps
- Linux amd64 arm64 (Ubuntu LTS release)
```
## TrustedPoint Services

| Parameter | Value
|-|-
| indexing | kv
| pruning | custom (100/17)
| min-retain-blocks | 0
| snapshot-interval | 2000
| snapshot-keep-recent | 2
| minimum-gas-prices | 0.01uward

---
- RPC: https://rpc-warden-testnet.trusted-point.com:443
- REST API: https://api-warden-testnet.trusted-point.com:443
- WSS: wss://rpc-warden-testnet.trusted-point.com:443/websocket
- P2P Persistent Peer: b314f4b177c5d52a831d2829fdb9d4f069475dca@peer-warden-testnet.trusted-point.com:29472
---
- State sync: [Guide](#state-sync)
- Fresh Snapshot: [URL](https://rpc-warden-testnet.trusted-point.com/latest_snapshot.tar.lz4) / [Guide](#download-snapshot) **(Being updated every 10 hours)**
- Fresh addrbook: [URL](https://rpc-warden-testnet.trusted-point.com/addrbook.json) / [Guide](#download-fresh-addrbookjson) **(Being updated every 5 minutes)**
- Genesis: [URL](https://rpc-warden-testnet.trusted-point.com/genesis.json) / [Guide](#download-fresh-addrbookjson)
- Live Peers scanner: [URL](https://rpc-warden-testnet.trusted-point.com/peers.txt) / [Guide](#add-fresh-persistent-peers) **(Being updated every 5 minutes)**

## Installation guide

### 1. Install required packages
```bash
sudo apt update && \
sudo apt install curl git jq build-essential gcc unzip wget lz4 -y
```
### 2. Install Go
```bash
cd $HOME && \
ver="1.21.3" && \
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && \
sudo rm -rf /usr/local/go && \
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && \
rm "go$ver.linux-amd64.tar.gz" && \
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile && \
source $HOME/.bash_profile && \
go version
```
### 3. Build `wardend` binary
```bash
git clone https://github.com/warden-protocol/wardenprotocol
cd  wardenprotocol
git checkout v0.3.0
make install
wardend version
```
### 4. Set up variables
```bash
# Customize if you need
echo 'export MONIKER="My_Node"' >> ~/.bash_profile
echo 'export CHAIN_ID="buenavista-1"' >> ~/.bash_profile
echo 'export WALLET_NAME="wallet"' >> ~/.bash_profile
echo 'export RPC_PORT="26657"' >> ~/.bash_profile
source $HOME/.bash_profile
```
### 5. Initialize the node
```bash
cd $HOME
wardend init $MONIKER --chain-id $CHAIN_ID
wardend config set client chain-id $CHAIN_ID
wardend config set client node tcp://localhost:$RPC_PORT
wardend config set client keyring-backend os # You can set it to "test" so you will not be asked for a password
```
### 6. Download genesis.json
```bash
wget https://rpc-warden-testnet.trusted-point.com/genesis.json -O $HOME/.warden/config/genesis.json
```
### 7. Add seeds and peers to the config.toml
```bash
PEERS="3f6e3d6f99c23487e797d28eb9d95e3cfb0b6e61@84.247.147.57:26656,22df256e71ba01bba80038c527a4f1103ad129d9@65.108.251.125:26656,ee528080741055cb7067f3e0bdda9badac834fc5@81.0.249.86:11256,ff13a301d956badc596de7145b19052f0965d62d@44.205.14.73:666,e9776f41f1682012555b86a3353db46188e19bc3@173.249.39.125:26656,89fbdc8995727e1c0d8525cdf087f1a6517f2685@168.119.10.134:29482,8973f6b31d3183daca419415a424604a5f67b8bd@138.201.51.154:30504,d4af4ec2657c9756c87aa5b49d2d724b45f96d8b@188.165.228.73:26656" && \
SEEDS="" && \
sed -i \
    -e "s/^seeds *=.*/seeds = \"$SEEDS\"/" \
    -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" \
    "$HOME/.warden/config/config.toml"
```
### 8. Change ports (Optional)
```bash
# Customize if you need
EXTERNAL_IP=$(wget -qO- eth0.me) \
PROXY_APP_PORT=26658 \
P2P_PORT=26656 \
PPROF_PORT=6060 \
API_PORT=1317 \
GRPC_PORT=9090 \
GRPC_WEB_PORT=9091
```
```bash
sed -i \
    -e "s/\(proxy_app = \"tcp:\/\/\)\([^:]*\):\([0-9]*\).*/\1\2:$PROXY_APP_PORT\"/" \
    -e "s/\(laddr = \"tcp:\/\/\)\([^:]*\):\([0-9]*\).*/\1\2:$RPC_PORT\"/" \
    -e "s/\(pprof_laddr = \"\)\([^:]*\):\([0-9]*\).*/\1localhost:$PPROF_PORT\"/" \
    -e "/\[p2p\]/,/^\[/{s/\(laddr = \"tcp:\/\/\)\([^:]*\):\([0-9]*\).*/\1\2:$P2P_PORT\"/}" \
    -e "/\[p2p\]/,/^\[/{s/\(external_address = \"\)\([^:]*\):\([0-9]*\).*/\1${EXTERNAL_IP}:$P2P_PORT\"/; t; s/\(external_address = \"\).*/\1${EXTERNAL_IP}:$P2P_PORT\"/}" \
    $HOME/.warden/config/config.toml
```
```bash
sed -i \
    -e "/\[api\]/,/^\[/{s/\(address = \"tcp:\/\/\)\([^:]*\):\([0-9]*\)\(\".*\)/\1\2:$API_PORT\4/}" \
    -e "/\[grpc\]/,/^\[/{s/\(address = \"\)\([^:]*\):\([0-9]*\)\(\".*\)/\1\2:$GRPC_PORT\4/}" \
    -e "/\[grpc-web\]/,/^\[/{s/\(address = \"\)\([^:]*\):\([0-9]*\)\(\".*\)/\1\2:$GRPC_WEB_PORT\4/}" \
    $HOME/.warden/config/app.toml
```
### 9. Configure prunning to save storage (Optional)
```bash
sed -i \
    -e "s/^pruning *=.*/pruning = \"custom\"/" \
    -e "s/^pruning-keep-recent *=.*/pruning-keep-recent = \"100\"/" \
    -e "s/^pruning-interval *=.*/pruning-interval = \"10\"/" \
    "$HOME/.warden/config/app.toml"
```
### 10. Set min gas price 
```bash
sed -i "s/^minimum-gas-prices *=.*/minimum-gas-prices = \"0.01uward\"/" $HOME/.warden/config/app.toml
```
### 11. Enable indexer (Optional)
```bash
sed -i "s/^indexer *=.*/indexer = \"kv\"/" $HOME/.warden/config/config.toml
```
### 12. Create a service file
```bash
sudo tee /etc/systemd/system/warden.service > /dev/null <<EOF
[Unit]
Description=Warden Node
After=network.target

[Service]
User=$USER
Type=simple
ExecStart=$(which wardend) start --home $HOME/.warden
Restart=on-failure
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
EOF
```
### 13. Start the node
```bash
sudo systemctl daemon-reload && \
sudo systemctl enable wardend && \
sudo systemctl restart wardend && \
sudo journalctl -u wardend -f -o cat
```
P.S. Consider [downloading snapshot](#download-snapshot) or using [state-sync](#state-sync) for the quick sync.

### 14. Create a wallet for your validator
```bash
wardend keys add $WALLET_NAME

# DO NOT FORGET TO SAVE THE SEED PHRASE
# You can add --recover flag to restore existing key instead of creating
```
### 15. Request tokens from the faucet
```bash
curl --data '{"address": "'$(wardend keys show $WALLET_NAME --bech acc -a)'"}' https://faucet.alfama.wardenprotocol.org
```

### 16. Check wallet balance
Make sure your node is fully synced unless it won't work.
```bash
wardend status | jq .SyncInfo.catching_up
```
```bash
wardend q bank balances $(wardend keys show $WALLET_NAME -a) 
```
17. Define variables to create validator.json file. Modify values if needed
```bash
pubkey=$(wardend tendermint show-validator)
amount="1000000uward"
moniker="MyNode"
identity="00000000"
website="https://google.com"
security="official@gmail.com"
details="Warden Validator"
commission_rate="0.1"
commission_max_rate="0.2"
commission_max_change_rate="0.01"
min_self_delegation="1"
```
### 18. Create JSON file
```bash
cat <<EOF > $HOME/.warden/config/validator.json
{
    "pubkey": $pubkey,
    "amount": "$amount",
    "moniker": "$moniker",
    "identity": "$identity",
    "website": "$website",
    "security": "$security",
    "details": "$details",
    "commission-rate": "$commission_rate",
    "commission-max-rate": "$commission_max_rate",
    "commission-max-change-rate": "$commission_max_change_rate",
    "min-self-delegation": "$min_self_delegation"
}
EOF

echo "validator.json file created successfully."
```

### 19. Make sure everything is correct
```bash
cat $HOME/.warden/config/validator.json
```

### 20. Create a validator
```bash
wardend tx staking create-validator $HOME/.warden/config/validator.json \
  --chain-id=$CHAIN_ID \
  --fees 30000uward \
  --gas 2000000 \
  --from $WALLET_NAME \
  -y
```
Do not forget to save `priv_validator_key.json` file located in $HOME/.warden/config/

## State sync

### 1. Stop the node
```bash
sudo systemctl stop wardend
```
### 2. Backup priv_validator_state.json 
```bash
cp $HOME/.warden/data/priv_validator_state.json $HOME/.warden/priv_validator_state.json.backup
```
### 3. Reset DB
```bash
wardend tendermint unsafe-reset-all --home $HOME/.warden --keep-addr-book
```
### 4. Setup required variables (One command)
```bash
PEERS="b314f4b177c5d52a831d2829fdb9d4f069475dca@peer-warden-testnet.trusted-point.com:29472" && \
RPC="https://rpc-warden-testnet.trusted-point.com:443" && \
LATEST_HEIGHT=$(curl -s --max-time 3 --retry 2 --retry-connrefused $RPC/block | jq -r .result.block.header.height) && \
TRUST_HEIGHT=$((LATEST_HEIGHT - 1500)) && \
TRUST_HASH=$(curl -s --max-time 3 --retry 2 --retry-connrefused "$RPC/block?height=$TRUST_HEIGHT" | jq -r .result.block_id.hash) && \

if [ -n "$PEERS" ] && [ -n "$RPC" ] && [ -n "$LATEST_HEIGHT" ] && [ -n "$TRUST_HEIGHT" ] && [ -n "$TRUST_HASH" ]; then
    sed -i.bak \
        -e "/\[statesync\]/,/^\[/{s/\(enable = \).*$/\1true/}" \
        -e "/^rpc_servers =/ s|=.*|= \"$RPC,$RPC\"|;" \
        -e "/^trust_height =/ s/=.*/= $TRUST_HEIGHT/;" \
        -e "/^trust_hash =/ s/=.*/= \"$TRUST_HASH\"/" \
        -e "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" \
        $HOME/.warden/config/config.toml
    echo -e "\nLATEST_HEIGHT: $LATEST_HEIGHT\nTRUST_HEIGHT: $TRUST_HEIGHT\nTRUST_HASH: $TRUST_HASH\nPEERS: $PEERS\n\nALL IS FINE"
else
    echo -e "\nError: One or more variables are empty. Please try again or change RPC\nExiting...\n"
fi
```
### 4. Move priv_validator_state.json back
```bash
mv $HOME/.warden/priv_validator_state.json.backup $HOME/.warden/data/priv_validator_state.json
```
### 5. Start the node
```bash
sudo systemctl restart wardend && sudo journalctl -u wardend -f -o cat
```
You should see the following logs. It may take up to 5 minutes for the snapshot to be discovered. If doesn't work, try downloading [snapshot](#download-snapshot)
```py
2:39PM INF sync any module=statesync msg="Discovering snapshots for 15s" server=node
2:39PM INF Discovered new snapshot format=3 hash="?^��I��\r�=�O�E�?�CQD�6�\x18�F:��\x006�" height=602000 module=statesync server=node
2:39PM INF Discovered new snapshot format=3 hash="%���\x16\x03�T0�v�f�C��5�<TlLb�5��l!�M" height=600000 module=statesync server=node
2:42PM INF VerifyHeader hash=CFC07DAB03CEB02F53273F5BDB6A7C16E6E02535B8A88614800ABA9C705D4AF7 height=602001 module=light server=node
```
After some time you should see the following logs. It make take 5 minutes for the node to catch up the rest of the blocks
```py
2:43PM INF indexed block events height=602265 module=txindex server=node
2:43PM INF executed block height=602266 module=state num_invalid_txs=0 num_valid_txs=0 server=node
2:43PM INF commit synced commit=436F6D6D697449447B5B31313720323535203139203132392031353920313035203136352033352031353320313220353620313533203139352031372036342034372033352034372032333220373120313939203720313734203620313635203338203336203633203235203136332039203134395D3A39333039417D module=server
2:43PM INF committed state app_hash=75FF13819F69A523990C3899C311402F232FE847C707AE06A526243F19A30995 height=602266 module=state num_txs=0 server=node
2:43PM INF indexed block events height=602266 module=txindex server=node
2:43PM INF executed block height=602267 module=state num_invalid_txs=0 num_valid_txs=0 server=node
2:43PM INF commit synced commit=436F6D6D697449447B5B323437203134322032342031313620323038203631203138362032333920323238203138312032333920313039203336203420383720323238203236203738203637203133302032323220313431203438203337203235203133302037302032343020313631203233372031312036365D3A39333039427D module=server
```
### 6. Check the synchronization status
```bash
wardend status | jq .SyncInfo
```
### 7. Disable state sync
```bash
sed -i.bak -e "/\[statesync\]/,/^\[/{s/\(enable = \).*$/\1false/}" $HOME/.warden/config/app.toml
```
## Download fresh addrbook.json

### 1. Stop the node and use `wget` to download the file
```bash
sudo systemctl stop wardend && \
wget -O $HOME/.warden/config/addrbook.json https://rpc-warden-testnet.trusted-point.com/addrbook.json
```
### 2. Restart the node
```bash
sudo systemctl restart wardend && sudo journalctl -u wardend -f -o cat
```
### 3. Check the synchronization status
```bash
wardend status | jq .SyncInfo
```
The file is being updated every 5 minutes

## Add fresh persistent peers

### 1. Extract persistent_peers from our endpoint
```bash
PEERS=$(curl -s --max-time 3 --retry 2 --retry-connrefused "https://rpc-warden-testnet.trusted-point.com/peers.txt")
if [ -z "$PEERS" ]; then
    echo "No peers were retrieved from the URL."
else
    echo -e "\nPEERS: "$PEERS""
    sed -i "s/^persistent_peers *=.*/persistent_peers = \"$PEERS\"/" "$HOME/.warden/config/config.toml"
    echo -e "\nConfiguration file updated successfully.\n"
fi
```
### 2. Restart the node
```bash
sudo systemctl restart wardend && sudo journalctl -u wardend -f -o cat
```
### 3. Check the synchronization status
```bash
wardend status | jq .SyncInfo
```
Peers are being updated every 5 minutes

## Download Snapshot

### 1. Download latest snapshot from our endpoint
```bash
wget https://rpc-warden-testnet.trusted-point.com/latest_snapshot.tar.lz4
```
### 2. Stop the node
```bash
sudo systemctl stop wardend
```
### 3. Backup priv_validator_state.json 
```bash
cp $HOME/.warden/data/priv_validator_state.json $HOME/.warden/priv_validator_state.json.backup
```
### 4. Reset DB
```bash
wardend tendermint unsafe-reset-all --home $HOME/.warden --keep-addr-book
```
### 5. Extract files fromt the arvhive 
```bash
lz4 -d -c ./latest_snapshot.tar.lz4 | tar -xf - -C $HOME/.warden
```
### 6. Move priv_validator_state.json back
```bash
mv $HOME/.warden/priv_validator_state.json.backup $HOME/.warden/data/priv_validator_state.json
```
### 7. Restart the node
```bash
sudo systemctl restart wardend && sudo journalctl -u wardend -f -o cat
```
### 8. Check the synchronization status
```bash
wardend status | jq .SyncInfo
```
Snapshot is being updated every 3 hours

## Useful commands
### Check node status 
```bash
wardend status | jq
```
### Query your validator
```bash
wardend q staking validator $(wardend keys show $WALLET_NAME --bech val -a) 
```
### Query missed blocks counter & jail details of your validator
```bash
wardend q slashing signing-info $(wardend tendermint show-validator)
```
### Unjail your validator 
```bash
wardend tx slashing unjail --from $WALLET_NAME --gas 2000000 --fees 30000uward -y
```
### Delegate tokens to your validator 
```bash 
wardend tx staking delegate $(wardend keys show $WALLET_NAME --bech val -a)  <AMOUNT>uward --from $WALLET_NAME --gas 2000000 --fees 30000uward -y
```
### Get your p2p peer address
```bash
wardend status | jq -r '"\(.NodeInfo.id)@\(.NodeInfo.listen_addr)"'
```
### Edit your validator
```bash 
wardend tx staking edit-validator --website="<WEBSITE>" --details="<DESCRIPTION>" --moniker="<NEW_MONIKER>" --from=$WALLET_NAME --gas 2000000 --fees 30000uward -y
```
### Send tokens between wallets 
```bash
wardend tx bank send $WALLET_NAME <TO_WALLET> <AMOUNT>uward --gas 2000000 --fees 30000uward -y
```
### Query your wallet balance 
```bash
wardend q bank balances $WALLET_NAME
```
### Monitor server load
```bash 
sudo apt update
sudo apt install htop -y
htop
```
### Query active validators
```bash
wardend q staking validators -o json --limit=1000 \
| jq '.validators[] | select(.status=="BOND_STATUS_BONDED")' \
| jq -r '.tokens + " - " + .description.moniker' \
| sort -gr | nl
```
### Query inactive validators
```bash
wardend q staking validators -o json --limit=1000 \
| jq '.validators[] | select(.status=="BOND_STATUS_UNBONDED")' \
| jq -r '.tokens + " - " + .description.moniker' \
| sort -gr | nl
```
### Check logs of the node
```bash
sudo journalctl -u wardend -f -o cat
```
### Restart the node
```bash
sudo systemctl restart wardend
```
### Stop the node
```bash
sudo systemctl stop wardend
```
### Upgrade the node
```bash
cd wardenprotocol
git fetch
git checkout tags/<version>
make install
wardend version
# Restrt the node
sudo systemctl restart wardend && sudo journalctl -u wardend -f -o cat
```
### Delete the node from the server
```bash
# !!! IF YOU HAVE CREATED A VALIDATOR, MAKE SURE TO BACKUP `priv_validator_key.json` file located in $HOME/.warden/config/ 
sudo systemctl stop wardend
sudo systemctl disable wardend
sudo rm /etc/systemd/system/wardend.service
rm -rf $HOME/.warden $HOME/wardenprotocol
```
### Example gRPC usage
```bash
wget https://github.com/fullstorydev/grpcurl/releases/download/v1.7.0/grpcurl_1.7.0_linux_x86_64.tar.gz
tar -xvf grpcurl_1.7.0_linux_x86_64.tar.gz
chmod +x grpcurl
./grpcurl  -plaintext  localhost:$GRPC_PORT list
### MAKE SURE gRPC is enabled in app.toml
# grep -A 3 "\[grpc\]" $HOME/.warden/config/app.toml
```
### Example REST API query
```bash
curl localhost:$API_PORT/cosmos/staking/v1beta1/validators
### MAKE SURE API is enabled in app.toml
# grep -A 3 "\[api\]" $HOME/.warden/config/app.toml
```

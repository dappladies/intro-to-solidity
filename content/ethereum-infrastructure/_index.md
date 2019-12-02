--- 
draft: false
title:  "Ethereum Infrastructure"
outputs: ["Reveal"]
---

# Welcome!
Ethereum Infrastructure Workshop: Spinning Up Your Own Blockchain

---

## Our Sponsor

![](./../images/dappladies/spring logo dark_new.png)

Thank you to Springlabs for sponsoring our event this evening!

{{% note %}}
- Spring Labs is building a protocol which allows participants such as financial institutions and consumers to share information such as credit and indentity data wihtout need to share the underlying data itself. They are an LA based company.
{{% /note %}}


---

### Agenda
- Why run a blockchain?
- What is a node?
- Ethereum Clients
- Consensus Protocols
- Genesis files
- Running an Ethereum Node

---

### Why Run a Blockchain
- Connect to mainnet

![](./../images/ethereuminfrastructure/EIW_diagram.png)

---

### Why Run a Blockchain
- Build a secure database for health records

![](./../images/ethereuminfrastructure/EIW_healthchain.png)

---

### Why Run a Blockchain
- Build a trustless database amongst untrusted parties

![](./../images/ethereuminfrastructure/EIW_databaseblockchain.png)

---

### Ethereum Node

- software that provides an entry point between the blockchain network and the developer or application
- provides an endpoint for mining, sending transactions, managing accounts, and more
- a node stores the blockchain database


{{% note %}}
A node is a piece of software that connects to other nodes, thus participating in the formation of the network. A node stores the blockchain, and a node may mine (but doesn't have to).
A node maintains a copy of the ethereum blockchain
{{% /note %}}


---

![](./../images/ethereuminfrastructure/EIW_nodes.png)

---

### Ethereum Clients

- The clients are simply software that implement the Ethereum protocol
- The most widely used Ethereum clients are
  - Geth (https://geth.ethereum.org/)
  - Parity (https://www.parity.io/ethereum/)


{{% note %}}
https://www.ethernodes.org/
https://github.com/ethereum/yellowpaper
{{% /note %}}

---

### Ethereum Consensus Protocols

- Proof of Work
- Proof of Stake
- Proof of Authority


{{% note %}}
https://blockgeeks.com/guides/blockchain-consensus/
The current Ethereum blockchain uses a consensus algorithm built specifically for the Ethereum blockchain called Ethash. The Ethash PoW algorithm introduces the property of “Memory Hardness” to the Ethereum blockchain.
In a Proof-of-Stake consensus algorithm, users who desire to validate blocks are required to deposit a stake of their own ether (right now, that stake is estimated to be 32 ether). That stake is locked, and a consensus algorithm is then used that only these staked users can participate in.
{{% /note %}}


---

### Proof of Work

- this algorithm is used to confirm transactions and produce new blocks to the chain
- miners confirm the transactions in the network and arrange blocks
- miners have to solve a complicated mathematical puzzle with a solution that is easy to verify but hard to find
- accurate work and speed of Blockchain system depend on it


{{% note %}}
https://cointelegraph.com/explained/proof-of-work-explained
{{% /note %}}

---

![](./../images/ethereuminfrastructure/cointelegraph_01.jpeg)

![](./../images/ethereuminfrastructure/cointelegraph_pow.png)

---

### Proof of Stake
- the algorithm uses a semi random election process to select a validator for the next block
- the election process is based on multiple factor including staking age, randomization, and the node’s wealth
- if the network detects a invalid block, the validator loses part of its stake
- energy efficient
- more people with less wealth can be validators

{{% note %}}
https://www.binance.vision/blockchain/proof-of-stake-explained
{{% /note %}}

---

### Proof of Authority
- a reputation-based consensus algorithm that introduces a practical and efficient solution for blockchain networks
- block validators are not staking coins but their own reputation instead
- validators are pre-set participants that are identified by their ethereum address
- works well for private blockchains


{{% note %}}
https://www.binance.vision/blockchain/proof-of-authority-explained
{{% /note %}}

---

### Setup your development environment

Create the project directory
```bash
mkdir ~/EthereumInfrastructure
```

Create the blockchain data directory
```bash
mkdir ~/EthereumInfrastructure/private
```

Create the keystore directory
```bash
mkdir ~/EthereumInfrastructure/private/keystore
```

---

### Install Dependencies

- Install Go  
  https://golang.org/dl/

- Install git  
  https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

---

### Verify Dependencies

After you install go, you will have to close your current terminal window and open a new terminal window to start using the go command.

Verify `go` is working (don't type in the dollar sign)
```bash
$ go
Go is a tool for managing Go source code.

Usage:

	go <command> [arguments]
...
```

---

### Download Geth from Source Code

- get the go-ethereum source code
- change directory into the code
- run the make all target, this will create binary files in the `go-ethereum/build/bin/` directory

```bash
git clone https://github.com/ethereum/go-ethereum.git ~/EthereumInfrastructure/

cd ~/EthereumInfrastructure/go-ethereum

make all

# Optional
export PATH="$PATH:~/EthereumInfrastructure/go-ethereum/build/bin/"
```

---

### Create Ethereum account

Create a password
```bash
cat /dev/urandom | env LC_CTYPE=C tr -dc a-zA-Z0-9 | head -c 24 > ~/EthereumInfrastructure/private/keystore/.passphrase
```

Generate an ethereum account
```bash
~/EthereumInfrastructure/go-ethereum/build/cmd/geth --datadir ~/EthereumInfrastructure/private account new --password ~/EthereumInfrastructure/private/keystore/.passphrase
```

---

### Create a genesis file

- A genesis block is the first block in the blockchain
- The genesis file defines the genesis block

![](./../images/ethereuminfrastructure/EIW_genesis.png)


---

### Create a Genesis File

Use the puppeth binary to start the interact prompts and create a genesis file.

```bash
$ ~/EthereumInfrastructure/go-ethereum/build/bin/puppeth
+-----------------------------------------------------------+
| Welcome to puppeth, your Ethereum private network manager |
|                                                           |
| This tool lets you create a new Ethereum network down to  |
| the genesis block, bootnodes, miners and ethstats servers |
| without the hassle that it would normally entail.         |
|                                                           |
| Puppeth uses SSH to dial in to remote servers, and builds |
| its network components out of Docker containers using the |
| docker-compose toolset.                                   |
+-----------------------------------------------------------+

Please specify a network name to administer (no spaces, hyphens or capital letters please)
> myblockchain

Sweet, you can set this via --network=myblockchain next time!

INFO [11-17|23:49:34.296] Administering Ethereum network           name=myblockchain
WARN [11-17|23:49:34.296] No previous configurations found         path=/Users/username/.puppeth/myblockchain

What would you like to do? (default = stats)
 1. Show network stats
 2. Configure new genesis
 3. Track new remote server
 4. Deploy network components
> 2

What would you like to do? (default = create)
 1. Create new genesis from scratch
 2. Import already existing genesis
> 1

Which consensus engine to use? (default = clique)
 1. Ethash - proof-of-work
 2. Clique - proof-of-authority
> 2

How many seconds should blocks take? (default = 15)
> 5

Which accounts are allowed to seal? (mandatory at least one)
> 0x1618Dca59FF9Aefe8bDd4E8887e7e06a8078bCFb
> 0x

Which accounts should be pre-funded? (advisable at least one)
> 0x1618Dca59FF9Aefe8bDd4E8887e7e06a8078bCFb
> 0x

Should the precompile-addresses (0x1 .. 0xff) be pre-funded with 1 wei? (advisable yes)
> yes

Specify your chain/network ID if you want an explicit one (default = random)
> 1234
INFO [11-17|23:58:17.882] Configured new genesis block

What would you like to do? (default = stats)
 1. Show network stats
 2. Manage existing genesis
 3. Track new remote server
 4. Deploy network components
> 2

 1. Modify existing configurations
 2. Export genesis configurations
 3. Remove genesis configuration
> 2

Which folder to save the genesis specs into? (default = current)
  Will create myblockchain.json, myblockchain-aleth.json, myblockchain-harmony.json, myblockchain-parity.json
>
INFO [11-17|23:59:42.873] Saved native genesis chain spec          path=myblockchain.json
ERROR[11-17|23:59:42.873] Failed to create Aleth chain spec        err="unsupported consensus engine"
ERROR[11-17|23:59:42.873] Failed to create Parity chain spec       err="unsupported consensus engine"
INFO [11-17|23:59:42.875] Saved genesis chain spec                 client=harmony path=myblockchain-harmony.json
```

---

### Genesis File Example

```
{
  "config": {
    "chainId": 1234,
    "homesteadBlock": 0,
    "eip150Block": 0,
    "eip150Hash": "0x0000000000000000000000000000000000000000000000000000000000000000",
    "eip155Block": 0,
    "eip158Block": 0,
    "byzantiumBlock": 0,
    "constantinopleBlock": 0,
    "petersburgBlock": 0,
    "istanbulBlock": 0,
    "clique": {
      "period": 5,
      "epoch": 30000
    }
  },
  "nonce": "0x0",
  "timestamp": "0x5dd24d3b",
  "extraData": "0x00000000000000000000000000000000000000000000000000000000000000001618dca59ff9aefe8bdd4e8887e7e06a8078bcfb0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
  "gasLimit": "0x47b760",
  "difficulty": "0x1",
  "mixHash": "0x0000000000000000000000000000000000000000000000000000000000000000",
  "coinbase": "0x0000000000000000000000000000000000000000",
  "alloc": {
    ...
  },
  "number": "0x0",
  "gasUsed": "0x0",
  "parentHash": "0x0000000000000000000000000000000000000000000000000000000000000000"
}
```

---

### Initialize the Ethereum Node

- The init command initializes a new genesis block and definition for the network.
- You only need to run this command once.

```bash
~/EthereumInfrastructure/go-ethereum/build/cmd/geth init ~/EthereumInfrastructure/private/genesis.json --datadir ~/EthereumInfrastructure/private/
```

---

### Start the Ethereum Node

Export your ethereum address
```bash
ETH_ADDRESS="1618dca59ff9aefe8bdd4e8887e7e06a8078bcfb"
```

Use the ETH_ADDRESS to start geth
```
~/EthereumInfrastructure/go-ethereum/build/cmd/geth --keystore ~/EthereumInfrastructure/private/keystore --networkid 1234 --unlock ${ETH_ADDRESS} --password ~/EthereumInfrastructure/private/keystore/.passphrase --datadir ~/EthereumInfrastructure/private/ --cache 1024 --port "30303" --rpc --rpcport 8545 --rpcaddr "0.0.0.0" --rpcvhosts "*" --rpccorsdomain "*" --targetgaslimit '800000000' --allow-insecure-unlock
```

Geth should be running now

---

### Interact with geth via the console

In another terminal window, attach the geth.ipc socket
```
$ ~/EthereumInfrastructure/go-ethereum/build/cmd/geth attach ~/EthereumInfrastructure/private/geth.ipc
Welcome to the Geth JavaScript console!

instance: Geth/v1.9.8-unstable-9e71f55b-20191117/darwin-amd64/go1.13.4
coinbase: 0x1618dca59ff9aefe8bdd4e8887e7e06a8078bcfb
at block: 0 (Sun, 17 Nov 2019 23:50:19 PST)
 datadir: /Users/username/Documents/git/ethereum_infrastructure/private
 modules: admin:1.0 clique:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0

> web3.eth.coinbase
"0x1618dca59ff9aefe8bdd4e8887e7e06a8078bcfb"

> web3.eth.getBalance(web3.eth.coinbase)
9.04625697166532776746648320380374280103671755200316906558262375061821325312e+74

> web3.eth.accounts
["0x1618dca59ff9aefe8bdd4e8887e7e06a8078bcfb"]

> web3.eth.sendTransaction({ from: web3.eth.coinbase, to: "0xe3322a8497c8157177affe0f6b8f2fb09d402e65",  value: web3.toWei(10000000, "ether")}

> web3.eth.getTransactionReceipt(hash [, callback])

> web3.eth.blockNumber
123

> exit
```

---

### Interact with Geth via RPC

```bash
curl -X GET -H "Content-Type: application/json" localhost:8545 --data '{"jsonrpc":"2.0","method":"eth_blockNumber", "params":[], "id":67 }'

curl -X GET -H "Content-Type: application/json" seth-miner.staging.springlabs.network:8545 --data '{"jsonrpc":"2.0","method":"eth_blockNumber", "params":[], "id":67 }' | jq -r '.result' | xargs -n1 printf '%d\n',

curl -X GET -H "Content-Type: application/json" prod-dcl-seth.springlabs.network:8545 --data '{"jsonrpc":"2.0","method":"eth_getTransactionCount", "params":['0x4129ade4f41099236c96FEa46eA7413fE60c3B41'], "id":67 }'
```

{{% note %}}
https://github.com/ethereum/wiki/wiki/JSON-RPC
{{% /note %}}

---

### Get enode

After your ethereum node has initialized
```
$ ~/EthereumInfrastructure/go-ethereum/build/cmd/geth attach geth.ipc
Welcome to the Geth JavaScript console!

instance: Geth/v1.9.8-unstable-9e71f55b-20191117/darwin-amd64/go1.13.4
coinbase: 0x1618dca59ff9aefe8bdd4e8887e7e06a8078bcfb
at block: 0 (Sun, 17 Nov 2019 23:50:19 PST)
 datadir: /Users/username/Documents/git/ethereum_infrastructure/private
 modules: admin:1.0 clique:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 txpool:1.0 web3:1.0

> admin.nodeInfo.enode
"enode://69f40ad0aa4cd732abfbce832fe9c38eab98b1d3b752a3f99b8c109b513b4c12aa97d021f6541450b0ac7a0b61e99c9350132948402bdce926887d04cd6f95f4@38.91.126.179:30303"
```

Enodes are shared amongst peers to tell nodes how to connect to each other.

---

### Kill the geth process

Get the geth process ID
```bash
$ ps aux | grep geth
username           PROCESS_ID   0.0  0.0  4408544    764 s001  S+   10:15PM   0:00.00 geth ...
```

Use the process ID to stop the geth process
```bash
kill -9 PROCESS_ID
```

---

### Let’s Start Our Own Chain!

---

### Sources
- https://www.binance.vision/blockchain/proof-of-authority-explained
- https://www.binance.vision/blockchain/proof-of-stake-explained
- https://cointelegraph.com/explained/proof-of-work-explained
- https://blockgeeks.com/guides/blockchain-consensus/
- https://www.ethernodes.org/
- https://github.com/ethereum/yellowpaper

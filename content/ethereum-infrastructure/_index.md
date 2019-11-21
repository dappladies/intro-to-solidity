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
```
mkdir ~/EthereumInfrastructure
```

Create the blockchain data directory
```
mkdir ~/EthereumInfrastructure/private
```

Create the keystore directory
```
mkdir ~/EthereumInfrastructure/private/keystore
```

---

### Install Dependencies

- Install Go  
  https://golang.org/dl/

- Install git  
  https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

---

### Download Geth from Source Code

```
cd ~/EthereumInfrastructure/go-ethereum/

git clone https://github.com/ethereum/go-ethereum.git

cd go-ethereum

make all

export PATH="$PATH:~/EthereumInfrastructure/go-ethereum/build/bin/"
```

---

### Create Ethereum account

Create a password
```
cat /dev/urandom | env LC_CTYPE=C tr -dc a-zA-Z0-9 | \  
head -c 24 > ~/EthereumInfrastructure/private/keystore/.passphrase
```

Generate an ethereum account
```
geth --datadir ~/EthereumInfrastructure/private account new \  
     --password ~/EthereumInfrastructure/private/keystore/.passphrase
```

---

### Create a genesis file

- A genesis block is the first block in the blockchain
- The genesis file defines the genesis block

![](./../images/ethereuminfrastructure/EIW_genesis.png)


---

### Create a Genesis File

```
puppeth
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
> testing

Sweet, you can set this via --network=testing next time!

INFO [11-17|23:49:34.296] Administering Ethereum network           name=testing
WARN [11-17|23:49:34.296] No previous configurations found         path=/Users/sdinay/.puppeth/testing

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
  Will create testing.json, testing-aleth.json, testing-harmony.json, testing-parity.json
>
INFO [11-17|23:59:42.873] Saved native genesis chain spec          path=testing.json
ERROR[11-17|23:59:42.873] Failed to create Aleth chain spec        err="unsupported consensus engine"
ERROR[11-17|23:59:42.873] Failed to create Parity chain spec       err="unsupported consensus engine"
INFO [11-17|23:59:42.875] Saved genesis chain spec                 client=harmony path=testing-harmony.json
```

---

### Initialize the Ethereum Node

- The init command initializes a new genesis block and definition for the network.
- You only need to run this command once.

```
geth init ~/EthereumInfrastructure/private/genesis.json --datadir ~/EthereumInfrastructure/private/
```

---

### Start the Ethereum Node

```
geth --keystore ~/EthereumInfrastructure/private/keystore \
  --networkid 1234 \
  --unlock YOUR_ADDRESS \
  --password ~/EthereumInfrastructure/private/keystore/.passphrase \
  --datadir ~/EthereumInfrastructure/private/ \
  --cache 1024 \
  --port "30303" \
  --rpc \
  --rpcport 8545 \
  --rpcaddr "0.0.0.0" \
  --rpcvhosts "*" \
  --rpccorsdomain "*" \
  --targetgaslimit '800000000' \
  --allow-insecure-unlock
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

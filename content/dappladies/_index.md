+++
title = "Intro To Solidity"
outputs = ["Reveal"]
+++

![](./../images/dappladies/logo.png)

Building a community of female developers in the blockchain space by providing educational opportunities for learn smart contract development.

---

# Intro To Solidity Part I
![](./../images/solidity.png)

---

# Satoshi Nakamoto
![](./../images/mystery-person.png)

In November 2008, Satoshi Nakamoto published a whitepaper titled [Bitcoin: A Peer-to-Peer Electonic Cash System](https://bitcoin.org/bitcoin.pdf). This laid the groundwork for the bitcoin protocol and the first blockchain database.

---

A blockchain is a time-stamped series of immutable record of data that is managed by a cluster of computers not owned by any single entity. Each of these blocks of data are secured and chained to each other using a cryptographic signature. You can think of this block chain as a ledger, which can be shared and accessed by anyone with the appropriate permissions.

---

# Key Points
- Distributed
- Decentralized
- Immutable
- Transparent

{{% note %}}
- Decentralized: no single one point where a decision is being made
- Distributed: the processing is shared across multiple nodes, but decisions can still be centralized
{{% /note %}}

---

<section data-noprocess>
  <h1>Why does it matter?</h1>
  <img src="./../images/earth.jpg" />
  <aside class="notes">
    “There are 2 billion people who have no bank accounts at all. There are another 4 billion people who have very limited access to banking. ​ Banking without international currencies, banking without international markets, banking without liquidity. Bitcoin isn’t about the 1 billion. Bitcoin is all about the other 6 1/2. The people who are currently cut off from international banking. What do you think happens when you suddenly are able to turn a simple text-messaging phone in the middle of a rural area in Nigeria, connected to a solar panel, into a bank terminal? Into a Western Union remittance terminal? ​Into an international loan-origination system? A stock market? An IPO engine? At first, nothing, but give it a few years.” 
    ― Andreas M. Antonopoulos, The Internet of Money
</aside>
</section>

---

# Ethereum
- Vitalik Buterin
- January 2014- Ethereum white paper released
- A new blockchain with a more general scripting lanuage

{{% note %}}
In the years following the bitcoin white paper, we have a few exchanges go up, we have a dude spend 10,000 bitcoins on a pizza, Silk Road gives crypto a bad name, Satoshi disappears, we have a few more blockchains pop up, and then, in 2014, 19 year old Vitalik Butern publishes the Ethereum white papers
{{% /note %}}

---

## Why Ethereum?
- Allows you to build applications that could run globally without any central authority
- Optimized for software developers!

{{% note %}}
Vitalik liked the idea of sending digital currency to one another, but he thought it would be even more useful to send it along with a story. "Sure, I'll send you this 1ETH, but only when you provide me with a document."
{{% /note %}}

---

## Applications
- financial applications
- semi-financial applications
- non financial applications

{{% note %}}
- financial applications: sub currencies, financial derivatives, savings wallets
- semi-financial applications: money involved, but also a heavy non-monetary side to what is being done
- non financial applications: online voting, decentralized governance
{{% /note %}}

---

## EVM
- Ethereum Virtual Machine
- One big computer

![](./../images/EVM.png)

{{% note %}}
Ethereum Virtual Machine: runtime environment that executes all of the smart contracts on the network
One big computer: made up of small computers all over
{{% /note %}}

---

## Traditional Web App Architecture
- insert picture

{{% note %}}
Almost everyone is familiar with this type of architecture. Web app is deployed on a server somewhere, and users who want to interact with that web app access the server.
{{% /note %}}

---

## Decentralized Ethereum Application
- insert picture

{{% note %}}
Ethereum Virtual Machine: runtime environment that executes all of the smart contracts on the network
One big computer: made up of small computers all over
{{% /note %}}

---

## Smart Contracts
- applications that can be deployed on the Ethereum blockchain
- written in Solidity
- compiled into EVM bytecode

{{% note %}}

{{% /note %}}

---

## Tools
- Remix
- Truffle Suite
- Parity
- Geth
- Test networks
- MetaMask

{{% note %}}

{{% /note %}}

---

## Remix
A browser-based compiler and IDE that enables users to build Ethereum contracts with Solidity language and to debug transactions.

https://remix.ethereum.org

---

## Truffle Suite
- Truffle: a development environment, testing framework and asset pipeline for blockchains using the EVM
- Ganache: a personal blockchain for Ethereum developers to deploy contracts, develop apps, and run tests
- Drizzle: a collection of front-end libraries that make writing dapp front-ends easier

https://truffleframework.com/

---

## Test Networks
- Ropsten- the one that most resembles the main network, uses Proof of Work consensus algorithm 
- Rinkeby- uses Proof of Authority consensus algorithm, you need to prove your existence in order to retrieve ethers
- Kovan- uses same consensus algorithm as Rinkeby

{{% note %}}
Test networks exist to ease development and provide developers and companies an easy solution to deliver their product on networks that are not exchanging real value but providing the exact same service.
{{% /note %}}

---

## Parity and Geth
- Both are Ethereum clients
- Full nodes that are capable of mining and signing transactions
- Parity written in Rust
- Geth written in Go

https://www.parity.io/ethereum/
https://geth.ethereum.org/downloads/

{{% note %}}
  The Ethereum protocol defines how the Ethereum network works, how clients should generally operate, and rules everyone must follow to be a valid part of the network. This protocol is written generally such that anyone could go and implement their own version of the protocol into a custom Ethereum client.
{{% /note %}}

---

## MetaMask
MetaMask is a browser plugin that allows users to make Ethereum transactions through regular websites. It allows you to run Ethereum dApps right in your browser without running a full Ethereum node. 

{{% note %}}

{{% /note %}}

---

## Let's Look at some code
![](./../images/dappladies/code.png)
{{% note %}}

{{% /note %}}

---

## Contracts
- Solidity's code is encapsulated in contracts
- all variables and functions belong to a contract
- compiled into EVM bytecode

```
pragma solidity ^0.5.0;

contract MyContract {

}
```

---

## State Variables
State variables are permanently stored in contract storage. This means they are written to the Ethereum blockchain.

```
pragma solidity ^0.5.0;

contract MyContract {
  uint value = 100;

}
```

---

## State Variables
Integers, structs, bools

```
pragma solidity ^0.5.0;

contract MyContract {
  uint value = 100;
  int value = -100;

  struct Person {
      uint age;
      string name;
    }
  
  bool exists;
}
```

---

## State Variables
Arrays

```
pragma solidity ^0.5.0;

contract MyContract {

  // Array with a fixed length;
  uint[2] fixedArray;

  // Dynamic array of integers;
  uint[] dynamicArray;

  // Dynamic array or strings;
  string[] stringArray;

  // Dynamic array of People structs;
  Person[] peopleArray;

  // public array;
  Person[] public peopleArray;

}
```

---

## State Variables: Address

- Ethereum blockchain is made up of accounts
- Each account has an address
- An account can be owned by a specific user or smart contract

```
0x0cE446255506E92DF41614C46F1d6df9Cc969183
```

```
contract MyContract {
  // owned by a user
  address public owner;

  // owned by a smart contract
  address public smartContract;

  // array of addresses
  address[] public players;
}
```

{{% note %}}
  Think of accounts like bank accounts. An account has a balance of Ether, and you can send and receive Ether payments o other accounts.
{{% /note %}}

---

## State Variables: Mappings

- A way of storing organized data in Solidity
- A mapping is essentially a key-value store for storing and looking up data

```
contract MyContract {

  // For a financial app, storing a uint that holds the user's account balance:
  mapping (address => uint) public accountBalance;
  
  // store / lookup usernames based on userId
  mapping (uint => string) userIdToName;

  // store / lookup to see if an address has voted
  mapping (address => bool) voted;

}
```

{{% note %}}

{{% /note %}}

---

## Global Variables
There are certain global variables that are available to all functions

```
msg.sender
msg.value
```

{{% note %}}

{{% /note %}}

---

## Storage vs Memory


{{% note %}}

{{% /note %}}

---

## Functions


{{% note %}}

{{% /note %}}

---

## Public vs Private


{{% note %}}

{{% /note %}}

---

## Return Values


{{% note %}}

{{% /note %}}

---

## Modifiers


{{% note %}}

{{% /note %}}

---

## Events


{{% note %}}

{{% /note %}}

---

## Require


{{% note %}}

{{% /note %}}

---

## Inheritance


{{% note %}}

{{% /note %}}

---

## Internal vs Private


{{% note %}}

{{% /note %}}

---

## Payable


{{% note %}}

{{% /note %}}

---

## Resources

{{% note %}}

{{% /note %}}

---

## Sources
- https://medium.com/coinmonks/ethereum-test-networks-69a5463789be


---



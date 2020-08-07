--- 
draft: false
title:  "Intro To Solidity"
outputs: ["Reveal"]
---

# Welcome!
Intro To Solidity

![](./../images/solidity.png)

---

### Agenda
- Introduction
- Blockchain basics
- Ethereum
- Dev Tools
- Smart Contract code

---

### About Me
- Wrote my first line of code in 2015
- Building smart contracts for 2.5 years
- Co-founder, Partner, & Software Developer at [Upstate Interactive](https://www.upstateinteractive.io)
- [DAppLadies](https://www.dappladies.com), [MetaGammaDelta DAO](https://www.dappladies.com), [saveDAI](https://www.dappladies.com)

---

### A Quick History Lesson...

---

### Cypherpunks
- Before the 1970s, cryptography was primarily practiced in secret by military or spy agencies
- 1992, first "Cypherpunk" meeting
- David Chaum: Digicash, Dr. Adam Back: Hashcash, Wei Dai: B-Money

{{% note %}}
- mailing list where they exchanged ideas and talked dev
- The basic ideas behind this movement can be found in the Cypherpunk manifesto written by Eric Hughes in 1993. The key principle which underpins the manifesto, is the importance of privacy. One can see this and other principles discussed in the manifesto being used to build the ideas that support some of the largest cryptocurrencies today.
{{% /note %}}

---

### Satoshi Nakamoto
![](./../images/mystery-person.png)

In November 2008, Satoshi Nakamoto published a whitepaper titled [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf).

{{% note %}}
- This laid the groundwork for the bitcoin protocol and the first blockchain database.
- double spend problem with digital currency - the same single digital token can be spent more than once since it's a digital file that can be duplicated and falsified. 
{{% /note %}}

---

### Blockchain
A blockchain is a time-stamped series of immutable records of data that is managed by a cluster of computers, not owned by any single entity. Each of these blocks of data are secured and chained to each other using a cryptographic signature. You can think of this blockchain as a ledger, which can be shared and accessed by anyone with the appropriate permissions.

{{% note %}}
- anyone is free to download the ledger on their computer and join the network, the transaction history is open for everyone to see
{{% /note %}}

---

### Key Points
![](./../images/dappladies/decentralized.png)
<p class="source">http://pages.cs.wisc.edu/~akella/CS740/F08/740-Papers/Bar64.pdf</p>

- Distributed
- Decentralized
- Immutable
- Transparent

{{% note %}}
- Distributed: the processing is shared across multiple nodes, but decisions can still be centralized
- Decentralized: no single one point where a decision is being made
{{% /note %}}

---

### Ethereum
![](./../images/dappladies/vitalik.jpg)

{{% note %}}
In the years following the bitcoin white paper, we have a few exchanges go up, we have a dude spend 10,000 bitcoins on a pizza, Silk Road gives crypto a bad name, Satoshi disappears, we have a few more blockchains pop up, and then, in 2014, 19 year old Vitalik Butern publishes the Ethereum white papers
{{% /note %}}

---
![](./../images/ethereumlogo.png)
### Ethereum
- A programmable blockchain
- Allows you to build applications that could run globally without any central authority
- Optimized for software developers!

{{% note %}}
Bitcoin blockchain is primarily used for sending money between various parties on the blockchain without the need for a central authority such as a bank.
Vitalik liked the idea of sending digital currency to one another, but he thought it would be even more useful to send it along with a story. "Sure, I'll send you this 1ETH, but only when you provide me with a document."
{{% /note %}}

---

### How does it work?
- Ethereum Virtual Machine
- One big computer

![](./../images/EVM.png)

{{% note %}}
At the heart of Ethereum is the EVM, Ethereum Virtuam Machine which executes all of the smart contracts on the network. 

One big computer: made up of small computers all over the world.

All these computers (also called nodes) are connected to one another and run the EVM. When you deploy your code on to the Ethereum blockchain, the code is replicated across all the nodes in the network. When your application stores any data, even that data is replicated across all the nodes. There are thousands of nodes in the network and it is almost impossible for anyone to stop all the nodes. This insures your application to be always accessible. 

{{% /note %}}

---

### Proof of Work and Mining
- Ethereum currently uses a system called “Proof of Work”. This allows the Ethereum network to agree on the state of all information recorded on the Ethereum blockchain, and prevents certain kinds of economic attacks.
- ETH 2.0, Ethereum will be moving to a different system called “Proof of Stake”

{{% note %}}

{{% /note %}}

---

### Traditional Web App Architecture
![](./../images/traditionalArchitecture.png)

{{% note %}}
One of the best ways to understand Ethereum is by comparing it with a traditional client/server architecture.
Almost everyone is familiar with this type of architecture. Web app is deployed on a server somewhere, and users who want to interact with that web app access the server.
{{% /note %}}

---

### Decentralized App Architecture
![](./../images/dappArchitecture.png)

{{% note %}}
every client (browser) communicates with its own instance of the application. There is no central server to which all clients connect to. Theoretically, to interact with a DApp you must have a copy of the blockchain downloaded on your computer. However, there have been many solutions in the community that allow you to hook up to the blockchain- meta mask, infura, hosted blockchain servers. 
2 main components of the Ethereum blockchain are the database and the code. Database: Every transaction in the network is stored in the blockchain. When you deploy your application, it is considered as a transaction. If you have for example a Voting application that allows anyone to vote for candidates, a vote for a candidate would be considered a transaction. 
Code: In Ethereum world, you write the logic/application code (called contract) in a language called Solidity. You then use the solidity compiler to compile it to Ethereum Byte Code and then deploy that byte code to the blockchain (There are few other languages you could use to write contracts but solidity is by far the most popular and relatively easier option). So, not only does Ethereum blockchain store the transactions, it also stores and executes the contract code.
{{% /note %}}

---

![](./../images/dappladies/smart-contract.jpg)

---

### Smart Contracts

immutable computer programs that run deterministically in the context of an Ethereum Virtual Machine as part of the Ethereum network protocol—i.e., on the decentralized Ethereum world computer

{{% note %}}
Let’s unpack that definition:

Computer programs
Smart contracts are simply computer programs. The word “contract” has no legal meaning in this context.

Immutable
Once deployed, the code of a smart contract cannot change. Unlike with traditional software, the only way to modify a smart contract is to deploy a new instance.

Deterministic
The outcome of the execution of a smart contract is the same for everyone who runs it, given the context of the transaction that initiated its execution and the state of the Ethereum blockchain at the moment of execution.

EVM context
Smart contracts operate with a very limited execution context. They can access their own state, the context of the transaction that called them, and some information about the most recent blocks.

Decentralized world computer
The EVM runs as a local instance on every Ethereum node, but because all instances of the EVM operate on the same initial state and produce the same final state, the system as a whole operates as a single "world computer."
{{% /note %}}

---

### Solidity
![](./../images/dappladies/solidity.png)

- object oriented programming language used to write smart contracts
- compiled into EVM bytecode
- influenced by C++, Python and Javascript
- statically typed, supports inheritance, libraries and complex user-defined types
- easy to learn for programmers

{{% note %}}

{{% /note %}}

---

### Gas

{{% note %}}

{{% /note %}}

---

### Tools
- Remix
- Truffle Suite
- Parity & Geth
- Test networks
- MetaMask

{{% note %}}

{{% /note %}}

---

### Remix
A browser-based compiler and IDE that enables users to build Ethereum contracts with Solidity language and to debug transactions.

https://remix.ethereum.org

{{% note %}}
Not only can you use it to as an editor but it can be used to compile and deploy your contracts to various networks and interact with them directly from the IDE. It has many features to select various compiler versions, debug your contracts and so on
{{% /note %}}

---

### Truffle Suite
- **Truffle**: a development environment, testing framework and asset pipeline for blockchains using the EVM
- **Ganache**: a personal blockchain for Ethereum developers to deploy contracts, develop apps, and run tests
- **Drizzle**: a collection of front-end libraries that make writing dapp front-ends easier

https://truffleframework.com/

{{% note %}}
Truffle is one of the most popular frameworks used to develop dapps. They abstract away lot of the complexities of compiling and deploying your contract on the blockchain. It also has an in-built testing framework you can use to test your contracts. 
Ganache- in-memory blockchain
{{% /note %}}

---

### Test Networks
- **Ropsten**: the one that most resembles the main network, uses Proof of Work consensus algorithm 
- **Rinkeby**: uses Proof of Authority consensus algorithm, you need to prove your existence in order to retrieve ethers
- **Kovan**: uses same consensus algorithm as Rinkeby

{{% note %}}
Test networks exist to ease development and provide developers and companies an easy solution to deliver their product on networks that are not exchanging real value but providing the exact same service.
{{% /note %}}

---

### Parity and Geth
- Ethereum clients
- Full nodes that are capable of mining and signing transactions
- Parity written in Rust
- Geth written in Go

https://www.parity.io/ethereum/
https://geth.ethereum.org/downloads/

{{% note %}}
  The Ethereum protocol defines how the Ethereum network works, how clients should generally operate, and rules everyone must follow to be a valid part of the network. This protocol is written generally such that anyone could go and implement their own version of the protocol into a custom Ethereum client.
  When you install and start the geth, parity or any other client, the EVM is started and it starts syncing, validating and executing transactions. 
{{% /note %}}

---

### MetaMask
![](./../images/metamask.png)

MetaMask is a browser plugin that allows users to make Ethereum transactions through regular websites. It allows you to run Ethereum dApps right in your browser without running a full Ethereum node. 

https://metamask.io/

{{% note %}}

{{% /note %}}

---

### Let's Look at some code
![](./../images/dappladies/token.png)

---

### Contracts
- Solidity's code is encapsulated in contracts
- all variables and functions belong to a contract

```
pragma solidity ^0.6.0;

// imports

contract MyContract {
  // events
  // variables
  // modifiers
  // constructor 
  // public functions
  // private functions
}
```

---

### Constructor

```
pragma solidity ^0.6.0;

contract MyContract {


}

{{% note %}}


{{% /note %}}
```

---

### State Variables
State variables are permanently stored in contract storage. This means they are written to the Ethereum blockchain.

```
pragma solidity ^0.6.0;

contract MyContract {
  uint256 public value = 100;
  int256 public value = -100;

  bytes32 public name;
  string public name;

  struct Person {
      uint age;
      string name;
      bool verified;
    }
  
  bool exists;

}

{{% note %}}
use bytes for arbitrary-length raw byte data
use string for arbitrary-length string (UTF-8) data

{{% /note %}}
```

---

### State Variables
Arrays

```
pragma solidity ^0.6.0;

contract MyContract {

  // Array with a fixed length;
  uint[2] fixedArray;

  // Dynamic array of integers;
  uint256[] dynamicArray;

  // Dynamic array or strings;
  string[] stringArray;

  // Dynamic array of People structs;
  Person[] peopleArray;

}
```

---

### State Variables: Address

- Ethereum blockchain is made up of accounts
- Each account has an address
- An account can be owned by a specific user or smart contract

```
0x4ef115373f9673D0757d18E30F04471B8C4AF35d
```

```
pragma solidity ^0.6.0;

contract MyContract {
  // owned by a user
  address public user;

  // owned by a smart contract
  address public smartContract;

  // array of addresses
  address[] public players;
}
```

{{% note %}}
  Think of accounts like bank accounts. An account has a balance of Ether, and you can send and receive Ether payments to other accounts.
{{% /note %}}

---

### State Variables: Mappings

- A way of storing organized data in Solidity
- A mapping is essentially a key-value store for storing and looking up data

```
pragma solidity ^0.6.0;

contract MyContract {

  // For a financial app, storing a uint that holds the user's account balance:
  mapping (address => uint256) public accountBalance;
  
  // store / lookup usernames based on userId
  mapping (uint256 => string) public userIdToName;

  // store / lookup to see if an address has voted
  mapping (address => bool) public voted;

  // how to set a mapping
  accountBalance[payeeAddress] = 1000;
  userIdToName[userId] = "Kseniya"

}
```

{{% note %}}

{{% /note %}}

---

### Global Variables
There are certain global variables that are available to all functions

```
msg.sender
msg.value
```

```
pragma solidity ^0.6.0;

contract MyContract {

  // store / lookup to see if an address has voted
  mapping (address => bool) public voted;

  function vote(string _candidate) {
    // voting code
    voted[msg.sender] = true;
  }

  // For a financial app, storing a uint that holds the user's account balance:
  mapping (address => uint256) public accountBalance;

  function sendFunds(address _to) {
    accountBalance[_to] = accountBalance[to].add(msg.value);
  }

}
```

{{% note %}}

{{% /note %}}

---

### Storage vs Memory
**Storage**: variables stored permanently to the blockchain
**Memory**: variables that are temporary and erased between external function calls

{{% note %}}
Most of the time you don't need to use these keywords because Solidity handles them by default. State variables (variables declared outside of functions) are by default storage and written permanently to the blockchain, while variables declared inside functions are memory and will disappear when the function call ends.
{{% /note %}}

---

### Functions

```
pragma solidity ^0.6.0;

contract MyContract {

  uint256 public userAge;
  string public userName;

  function addUser(string name, uint256 age) {
    userAge = age;
    userName = name;
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}

{{% /note %}}

---

### Return Values
```
pragma solidity ^0.6.0;

contract MyContract {

  uint256 public userAge;
  string public userName;

  function addUser(string _name, uint _age) {
    userAge = _age;
    userName = _name;
  }
  
  function getAge() public returns (uint) {
    return userAge;
  }

  addUser("Kseniya", 33);
  // returns 33;
  getAge();
}
```

---

### Events
Events are a way for your contract to communicate what happened on the blockchain to your front-end, which can be listening for events and take action when they happen. 

```
pragma solidity ^0.6.0;

contract MyContract {

  event UserAdded(string name, uint256 age);

  uint public userAge;
  string public userName;

  function addUser(string name, uint256 age) {
    userAge = age;
    userName = name;
    emit UserAdded( name, age)
  }

  addUser("Kseniya", 33);
}
```

---

### Require
```
pragma solidity ^0.6.0;

contract MyContract {

  uint256 public userAge;
  string public userName;

  // userAddress to boolean
  mapping (address => bool) public userExists;

  function addUser(string name, uint256 age) public {
    require(userExists[msg.sender] == false);
    userAge = age;
    userName = name;
    userExists[msg.sender] = true;
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}
require can be used to check for conditions and throw an exception if the condition is not met.
{{% /note %}}

---

### Modifiers
Modifier are like a prerequisites check of the function
```
pragma solidity ^0.6.0;

contract MyContract {

  uint256 public userAge;
  string public userName;

  // userAddress to boolean
  mapping (address => bool) public userExists;

  modifier onlyNewUser {
      require(userExists[msg.sender] == false);
      _;
  }

  function addUser(string name, uint256 age) public onlyNewUser {
    userAge = age;
    userName = name;
    userExists[msg.sender] = true;
  }

  addUser("Kseniya", 33);
}

```

---

### Inheritance
Inheritance can be used for logical inheritance (subclass) or for organizing your code to group similar logic.

```
pragma solidity ^0.6.0;

contract Ownable {

  address public owner;

  function setOwner() public {
    owner = msg.sender;
  }
}

contract MyContract is Ownable {

  uint public userAge;
  uint public userName;

  function addUser(string name, uint256 age) public {
    userAge = age;
    userName = name;
  }
}

```

{{% note %}}

{{% /note %}}

---

### Public vs Private
**Public**: anyone or any contract can call your contract's function
**Private**: only a function in the contract can call the function

```
pragma solidity ^0.6.0;

contract MyContract {

  uint private _userAge;
  string private _userName;

  function addUser(string _name, uint _age) public {
    _addUser(_name, _age)
  }

  function _addUser(string _name, uint _age) private {
    _userAge = _age;
    _userName = _name;
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}

{{% /note %}}

---

### Internal vs External
`private, public, internal, external`

**Internal**- the same as private, except it's also accessible to contract that inherit from this contract.

**External**- similar to public, except these functions can ONLY be called outside the contract.

{{% note %}}
For declaring internal or external functions, the syntax is the same as private and public
{{% /note %}}

---

### Internal vs External

```
contract Ownable {

  address public owner;

  function setOwner() internal {
    owner = msg.sender;
  }
}

contract MyContract is Ownable {

  uint public userAge;
  uint public userName;
  
  function addUser(string _name, uint _age) public {
    userAge = _age;
    userName = _name;
  }
  // we can call this function
  setOwner();
}

```

---

### Resources: Let's Code!

```
git clone https://github.com/dappladies/su-token.git
npm i

```
---

![](./../images/meme.jpg)

---

### Resources: Tutorials

[CryptoZombies](https://cryptozombies.io/en/course)

[Solidity Docs](https://solidity.readthedocs.io/en/v0.5.6/)

[Upstate Interactive Medium](https://medium.com/upstate-interactive)

---

### Resources: Books

[The Internet of Money](https://www.amazon.com/gp/product/B01L9WM0H8?pf_rd_p=d1f45e03-8b73-4c9a-9beb-4819111bef9a&pf_rd_r=RBT6834KKM1E19W1HZ26)

[The Infinite Machine](https://www.amazon.com/Infinite-Machine-Crypto-hackers-Building-Internet/dp/0062886142/ref=sr_1_1?crid=38OHSEEGE6Z2N&dchild=1&keywords=the+infinite+machine+camila+russo&qid=1596822314&sprefix=the+infinite+machine%2Caps%2C171&sr=8-1)

[Digital Gold: Bitcoin and the Inside Story of the Misfits and Millionaires Trying to Reinvent Money](https://www.amazon.com/Digital-Gold-Bitcoin-Millionaires-Reinvent/dp/006236250X/ref=sr_1_1?crid=2PUINNZOQ5RHB&dchild=1&keywords=digital+gold&qid=1596822357&sprefix=digital+gold%2Caps%2C159&sr=8-1)

---

### Questions?

---

### Sources
- https://medium.com/coinmonks/ethereum-test-networks-69a5463789be
- https://blockgeeks.com/guides/what-is-blockchain-technology/
- https://cryptozombies.io/en/course




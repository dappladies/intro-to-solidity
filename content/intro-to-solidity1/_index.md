--- 
draft: false
title:  "Intro To Solidity Part I"
outputs: ["Reveal"]
---

# Welcome!
Intro To Solidity Part I

![](./../images/solidity.png)

---

## Our Sponsor

![](./../images/dappladies/spring logo dark_new.png)

Thank you to Springlabs for sponsoring our event this evening!

{{% note %}}
- Spring Labs is building a protocol which allows participants such as financial institutions and consumers to share information such as credit and indentity data wihtout need to share the underlying data itself. They are an LA based company.
{{% /note %}}


---

### Agenda
- Introductions
- Blockchain basics
- Ethereum
- Dev Tools
- Smart Contract code

---

![](./../images/dappladies/logo.png)


- <a href="https://www.linkedin.com/in/kseniya-lifanova-aa50b19/" target="_blank">Kseniya Lifanova</a>: Co-founder, Partner and Software Developer at Upstate Interactive, Founder of DAppLadies
- <a href="https://www.linkedin.com/in/swati-mazumder-015783b/" target="_blank">Swati Mazumder</a>: Founder at SyncSol | Developer, Analyst, Technology Enthusiast, DAppLadies Member
- <a href="https://www.linkedin.com/in/sdinay/" target="_blank">Shanee Dinay</a>: Software Engineer at Spring Labs, DAppLadies Member

---

### Satoshi Nakamoto
![](./../images/mystery-person.png)

In November 2008, Satoshi Nakamoto published a whitepaper titled [Bitcoin: A Peer-to-Peer Electronic Cash System](https://bitcoin.org/bitcoin.pdf). This laid the groundwork for the bitcoin protocol and the first blockchain database.

{{% note %}}
- double spend problem with digital currency - the same single digital token can be spent more than once since it's a digital file that can be duplicated and falsified. 
{{% /note %}}

---

### Blockchain
A blockchain is a time-stamped series of immutable records of data that is managed by a cluster of computers not owned by any single entity. Each of these blocks of data are secured and chained to each other using a cryptographic signature. You can think of this blockchain as a ledger, which can be shared and accessed by anyone with the appropriate permissions.

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

### Ethereum
- A new blockchain with a more general scripting lanuage
- Allows you to build applications that could run globally without any central authority
- Optimized for software developers!

{{% note %}}
Bitcoin blockchain is primarily used for sending money between various parties on the blockchain without the need for a central authority such as a bank.
Vitalik liked the idea of sending digital currency to one another, but he thought it would be even more useful to send it along with a story. "Sure, I'll send you this 1ETH, but only when you provide me with a document."
{{% /note %}}

---

### EVM
- Ethereum Virtual Machine
- One big computer


![](./../images/EVM.png)

{{% note %}}
At the heart of Ethereum is the EVM, Ethereum Virtuam Machine which executes all of the smart contracts on the network. 

One big computer: made up of small computers all over the world.
All these computers (also called nodes) are connected to one another and run the EVM. When you deploy your code on to the Ethereum blockchain, the code is replicated across all the nodes in the network. When your application stores any data, even that data is replicated across all the nodes. There are thousands of nodes in the network and it is almost impossible for anyone to stop all the nodes. This insures your application to be always accessible. 

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

### Applications
- financial applications
- semi-financial applications
- non financial applications

{{% note %}}
Because Ethereum is a programmable blockchain, you can build all different types of applications.
- financial applications: sub currencies, financial derivatives, savings wallets
- semi-financial applications: money involved, but also a heavy non-monetary side to what is being done
- non financial applications: online voting, decentralized governance
{{% /note %}}

---

### Smart Contracts
![](./../images/dappladies/smart-contract.jpg)

- applications that can be deployed on the Ethereum blockchain
- written in Solidity
- compiled into EVM bytecode

{{% note %}}
In Ethereum, we can write applications in the Solidity programming language and deploy it on to the Ethereum blockchain. These applications are called Smart Contracts.

In general, contract is a written agreement between two or many parties that is intended to be enforced by law. If we take this written contract and translate it in to code and deploy on the blockchain, we get digital contracts.
{{% /note %}}

---

### Solidity
![](./../images/dappladies/solidity.png)

- object oriented programming language used to write smart contracts
- influenced by C++, Python and Javascript
- easy to learn for programmers

{{% note %}}

{{% /note %}}

---

### Tools
- Remix
- Truffle Suite
- Parity
- Geth
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
Ganahce- in-memory blockchain
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
- Both are Ethereum clients
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
{{% note %}}

{{% /note %}}

---

### Contracts
- Solidity's code is encapsulated in contracts
- all variables and functions belong to a contract
- compiled into EVM bytecode

```
pragma solidity ^0.5.0;

contract MyContract {

}
```

---

### State Variables
State variables are permanently stored in contract storage. This means they are written to the Ethereum blockchain.

```
pragma solidity ^0.5.0;

contract MyContract {
  uint value = 100;
  int value = -100;

  struct Person {
      uint age;
      string name;
      bool verified;
    }
  
  bool exists;

}
```

---

### State Variables
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

}
```

---

### State Variables: Address

- Ethereum blockchain is made up of accounts
- Each account has an address
- An account can be owned by a specific user or smart contract

```
0x0cE446255506E92DF41614C46F1d6df9Cc969183
```

```
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

### Global Variables
There are certain global variables that are available to all functions

```
msg.sender
msg.value
```

```
contract MyContract {

  // store / lookup to see if an address has voted
  mapping (address => bool) voted;

  function vote(string _candidate) {
    // code
    voted[msg.sender] = true;
  }

  // For a financial app, storing a uint that holds the user's account balance:
  mapping (address => uint) public accountBalance;

  function sendFunds(address _to) {
    accountBalance[_to] = _accountBalance[to].add(msg.value);
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
contract MyContract {

  uint public userAge;
  string public userName;

  function addUser(string _name, uint _age) {
    userAge = _age;
    userName = _name;
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}

{{% /note %}}

---

### Public vs Private
**Public**: anyone or any contract can call your contract's function
**Private**: only you or a function in your contract can call the function

```
contract MyContract {

  uint private userAge;
  string private userName;

  function _addUser(string _name, uint _age) private {
    userAge = _age;
    userName = _name;
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}

{{% /note %}}

---

### Return Values
```
contract MyContract {

  uint public userAge;
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
{{% note %}}

{{% /note %}}

---

### Modifiers
Modifier are like a prerequisites check of the function
```
contract MyContract {

  uint public userAge;
  string public userName;

  function addUser(string _name, uint _age) {
    userAge = _age;
    userName = _name;
  }
  
  function getAge() public view returns (uint) {
    return userAge;
  }

  function _multiply(uint a, uint b) private pure returns (uint) {
    return a * b;
  }

  function getAge() public onlyOwner returns (uint) {
    return userAge;
  }

  addUser("Kseniya", 33);
}
```

---

### Events
Events are a way for your contract to communicate what happened on the blockchain to your front-end, which can be listening for events and take action when they happen. 

```
contract MyContract {
  event UserAdded(string _name, uint _age);

  uint public userAge;
  string public userName;

  function addUser(string _name, uint _age) {
    userAge = _age;
    userName = _name;
    emit UserAdded( _name, _age)
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}

{{% /note %}}

---

### Require
```
contract MyContract {

  uint public userAge;
  string public userName;
  address public userAddress;

  // userAddress to boolean
  mapping (address => bool) public userExists;

  function addUser(string _name, uint _age) {
    require(userExists[msg.sender] == false);
    userAge = _age;
    userName = _name;
    userAddress = msg.sender;
    userExists[msg.sender] = true;
  }

  addUser("Kseniya", 33);
}
```

{{% note %}}

{{% /note %}}

---

### Inheritance
Inheritance can be used for logical inheritance (subclass) or for organizing your code to group similar logic.

```
contract Ownable {

  address public owner;

  function setOwner() public {
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

![](./../images/meme.jpg)

---

### Why does it matter?
![](./../images/earth.jpg)

{{% note %}}
There are 2 billion people who have no bank accounts at all. There are another 4 billion people who have very limited access to banking. ​ Banking without international currencies, banking without international markets, banking without liquidity. Bitcoin isn’t about the 1 billion. Bitcoin is all about the other 6 1/2. The people who are currently cut off from international banking. What do you think happens when you suddenly are able to turn a simple text-messaging phone in the middle of a rural area in Nigeria, connected to a solar panel, into a bank terminal? Into a Western Union remittance terminal? ​Into an international loan-origination system? A stock market? An IPO engine? At first, nothing, but give it a few years
    ― Andreas M. Antonopoulos, The Internet of Money
{{% /note %}}

---

### Resources

[CryptoZombies](https://cryptozombies.io/en/course)

[Zastrin](https://www.zastrin.com)

[Solidity Docs](https://solidity.readthedocs.io/en/v0.5.6/)

[The Internet of Money](https://www.amazon.com/gp/product/B01L9WM0H8?pf_rd_p=d1f45e03-8b73-4c9a-9beb-4819111bef9a&pf_rd_r=RBT6834KKM1E19W1HZ26)

[Upstate Interactive Medium](https://medium.com/upstate-interactive)

---

### Next Class

We will be building a Payment DApp!

---

### Homework
Make sure you have [node](https://nodejs.org/en/download/current/) installed.

Install a Solidity extension for your text editor:

- [Link for VSCode](https://marketplace.visualstudio.com/items?itemName=JuanBlanco.solidity) 
- [Link for Sublime](https://packagecontrol.io/packages/Ethereum)

`npm install -g truffle`

`npm install -g ganache-cli`

`npm install openzeppelin-solidity`



---

### Sources
- https://medium.com/coinmonks/ethereum-test-networks-69a5463789be
- https://blockgeeks.com/guides/what-is-blockchain-technology/
- https://cryptozombies.io/en/course




--- 
draft: false
title:  "Intro To Solidity Part II"
outputs: ["Reveal"]
---

# Welcome!
Intro To Solidity Part II

![](./../images/solidity.png)

---

## Our Sponsor

![](./../images/dappladies/spring logo dark_new.png)

Thank you to Springlabs for sponsoring our event this evening!

{{% note %}}
- Spring Labs is building a protocol which allows participants such as financial institutions and consumers to share information such as credit and indentity data wihtout need to share the underlying data itself. They are an LA based company.
{{% /note %}}


---

### Payment App
Today we will be building a payment application! This app will be able to:

- create users
- allows users to add friends
- allow users to create events
- allow users to join events
- allow event participants to add funds
- split and distribute refunds at the end of the event.

---

### Dev Environemnt
Make sure you have [node](https://nodejs.org/en/download/current/) installed.

Install a Solidity extension for your text editor:

- [Link for VSCode](https://marketplace.visualstudio.com/items?itemName=JuanBlanco.solidity) 
- [Link for Sublime](https://packagecontrol.io/packages/Ethereum)

`npm install -g truffle`

`npm install -g ganache-cli`

`npm install openzeppelin-solidity`

`npm install web3`

---

### Create folder 

`mkdir paymentApp`

`cd paymentApp`

`truffle init`

`cd contracts`

`touch UserFactory.sol`

---

### Create folder 

```
pragma solidity >=0.4.0 <0.6.0;

contract UserFactory  {

  struct User {
    string userName;
    address[] friends;
  }

  // dynamic array of all user addresses
  address[] public userAddresses;

  // map an address to their User struct
  mapping (address => User) public userStruct;

  // mapping of an user address to boolean
  mapping (address => bool) public isUser;

  // map of users to friends
  mapping (address => address) public userToFriend;

  constructor() public {}

  function createUser(string memory _name) public {
    // add user address to array
    userAddresses.push(msg.sender);

    // set userName
    userStruct[msg.sender].userName = _name;

    // set isUser mapping to true
    isUser[msg.sender] = true;
  }
}
```

---

### Inside the folder 

- contracts/ hold the Solidity files (or Vyper)
- migrations/ hold migration files that are used to deploy smart contracts to the blockchain
- test/ folder is where you put your unit tests
- truffle-config.js is a config file where you connect to an Ethereum network

{{% note %}}
We are importing the MyContract Solidity file and using a deployer object provided by Truffle to deploy said contract onto a blockchain.

Contracts are developed within the contracts folder, before being migrated onto a blockchain, and then tested using Truffle’s automated testing capabilities. 

By default Truffle Develop runs on localhost:9545 whereas Ganache runs on localhost:8545.

{{% /note %}}

---

### Inside the folder 

Add a file called `2_deploy_contracts.js` to migrations folder

```
const UserFactory = artifacts.require("./UserFactory.sol");

module.exports = function(deployer) {
  deployer.deploy(UserFactory);
};
```

{{% note %}}
The very first migration 1_initial_migration.js deploys a contract named Migrations to the blockchain and is used to store the latest contract you have deployed. Every time you run the migration, truffle queries the blockchain to get the last contract that has been deployed and then deploys any contracts which haven’t been deployed yet. It then updates the last_completed_migration field in the Migrations contract to indicate the latest contract deployed. You can simply think of it as a database table called Migration with a column named last_completed_migration which is kept up to date always. You can find more details on the truffle documentation page.
{{% /note %}}

---

### Next

- `truffle migrate`
- `truffle console`
- `web3.eth.getAccounts()`
- `web3.eth.getBalance(address)`
- `web3.utils.fromWei('100000000000000000000', 'ether')`
- `UserFactory.address`

---

### Let's add some functions!

- `addFriends`
- `getMyFriends`
- `createEvent`
- `joinEvent`
- `getEventParticipants`
- `addFundsToEvent`
- `endEvent`
- `_distributeFunds`



---

### Sources
- https://medium.com/@mvmurthy/full-stack-hello-world-voting-ethereum-dapp-tutorial-part-1-40d2d0d807c2
- https://web3js.readthedocs.io/en/1.0/web3-eth-contract.html#eth-contract
- https://truffleframework.com/docs/truffle/reference/truffle-commands
- https://cryptozombies.io/en/course
- https://medium.com/@rossbulat/introduction-to-the-truffle-suite-and-dapp-development-pipeline-1b33bb8228d4




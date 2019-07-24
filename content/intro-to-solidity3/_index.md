--- 
draft: false
title:  "Intro To Solidity Part III"
outputs: ["Reveal"]
---

# Welcome!
Intro To Solidity Workshop (Part III)

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
Today we will continue to work on our PaymentApp. 

Functions:

```
createUser
addFriend
getMyFriends
createEvent
getEventInfo
joinEvent
getEventParticipants
addFundsToEvent
endEvent
withdraw
deposit
_isEventParticipant
_calculateSplit
```

---

### Review: Developer Tools
- **Truffle**: a development environment, testing framework and asset pipeline for blockchains using the EVM
- **Ganache**: a personal blockchain for Ethereum developers to deploy contracts, develop apps, and run tests
- **Remix**: A browser-based compiler and IDE that enables users to build Ethereum contracts with Solidity language and to debug transactions.
- **Parity & Geth**: Ethereum clients that are capable of mining and signing transactions
- **Test networks**: Ropsten, Rinkeby, Kovan
- **MetaMask:** a browser plugin that allows users to make Ethereum transactions through regular websites

---

### Review: Global & State Variables 

```
pragma solidity >=0.4.0 <0.6.0;

contract UserFactory  {

  struct User {
    string userName;
    address[] friends;
    uint256 numOfFriends;
  }

  address[] public userAddresses;

  mapping (address => User) public userStruct;
  mapping (address => bool) public isUser;

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

### Review: Public vs Private vs Internal vs External
**Public**: anyone or any contract can call your contract's function

**Private**: only you or a function in your contract can call the function

**Internal**: the same as private, except it's also accessible to contract that inherit from this contract.

**External**: similar to public, except these functions can ONLY be called outside the contract.

---

### Payable and Transfer
- to send ether to a smart contract, you need a no name function called a fallback function

`function() payable {}`

- Or, you can add the payable modifier to a function that you want to call as well as send value to.

- the `transfer()` function transfers eth to an address

`address.transfer(amount)`

---

### Testing 

- testing in the terminal
- writing unit tests
- using remix-ide and web3

---

### Let's Code!

---

### Sources
- https://medium.com/@mvmurthy/full-stack-hello-world-voting-ethereum-dapp-tutorial-part-1-40d2d0d807c2
- https://web3js.readthedocs.io/en/1.0/web3-eth-contract.html#eth-contract
- https://truffleframework.com/docs/truffle/reference/truffle-commands
- https://cryptozombies.io/en/course
- https://medium.com/@rossbulat/introduction-to-the-truffle-suite-and-dapp-development-pipeline-1b33bb8228d4




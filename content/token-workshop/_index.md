--- 
draft: false
title:  "Token Workshop"
outputs: ["Reveal"]
---

# Welcome!
Solidity Workshop: ERC20 & ERC721 Token Workshop

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
- Build and deploy your own ERC20 Token
- Build and deploy your own ERC721 Token
- Send tokens to each other
- Build an ERC1155 token 

---

### Tokens
- Tokens are digital assets that are built on top of the Ethereum blockchain
- They are a representation of something on the blockchain
- Examples: money, physical objects such as cars, services, shares in a company, a virtual pet

{{% note %}}
You can compare the Ethereum platform and the tokens built on top of it as the App Store providing a platform for iOS apps, where you could build an app with some digital currency used within the game. 
{{% /note %}}

---

### Token Contracts

- A token contract is simply an Ethereum smart contract
- Sending tokens actually means “calling a function on a smart contract that someone wrote and deployed”
- Token contracts have mappings that map user addresses to their balance

{{% note %}}
It is these balances that represent the tokens themselves. Someone "has tokens" when their balance in the token contract is non-zero. That’s it! 
{{% /note %}}


---

### Kinds of Tokens

- The major difference between tokens is fungibility
- Fungible tokens vs nonfungible tokens
- Tokens that are fungibile are equivalent and interchangeable

![](./../images/dappladies/dollar.jpg)

{{% note %}}
Fungible goods are equivalent and interchangeable, like Ether, fiat currencies, and voting rights.
{{% /note %}}

---

### Kinds of Tokens

- Tokens that are non-fungible are tokens that contain a unique characteristics
- No 2 tokens are the same

![](./../images/dappladies/cryptokitty.png)

{{% note %}}
In a nutshell, when dealing with non-fungibles (like your house) you care about which ones you have, while in fungible assets (like your bank account statement) what matters is how much you have.
{{% /note %}}


---

### Standards

- The community has developed a variety of standards (EIPs or ERCs) that developers can use when creating their own tokens
- by using standards, tokens can be compatible with other platforms like cryptocurreny exchanges
- ERC20 is a standard interface for fungible tokens
- ERC721 is a standard interface for nonfungible tokens

https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts

{{% note %}}
EIP stands for Ethereum Improvement Proposal
ERC - application-level standards and conventions, including contract standards such as token standards
{{% /note %}}

---

### Let's Code!
- MetaMask
- https://faucet.ropsten.be/

- `mkdir token_workshop` 
- `cd token_workshop`
- `truffle unbox`
- `npm init`
- `npm install @openzeppelin/contracts`
- `npm install truffle-flattener`

---

### Sources
- https://blockgeeks.com/guides/ethereum-token/
- https://docs.openzeppelin.com/contracts/2.x/tokens

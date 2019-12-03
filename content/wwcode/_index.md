--- 
draft: false
title:  "WWCode Workshop"
outputs: ["Reveal"]
---

<head>
<!-- Place your kit's code here -->
<script src="https://kit.fontawesome.com/7830f75e01.js" crossorigin="anonymous"></script>
</head>

# Token Development: 
#### A Crash Course Introduction

Kseniya Lifanova

![](./../images/sbbs/cover.png)

---

### About Me
- Wrote my first line of code in 2015
- Co-founder, Partner, & Software Developer at <a href="https://www.upstateinteractive.io" target ="_blank">Upstate Interactive</a>
- Founder of <a href="https://www.dappladies.com" target ="_blank">DAppLadies</a>

<img src="./../images/sbbs/sm-grad-logo.png" class="about_img"/>
<img src="./../images/sbbs/logo.png" class="about_img"/>

---

### Agenda
- Tokens
- How to make a token?
  - Smart Contracts
  - Developer Tools
  - Token Standards
- Build and deploy your own ERC20 Token
- Build and deploy your own ERC721 Token

---

### Tokens
- Tokens are programmable assets that are built on top of a blockchain
- They are a representation of something on the blockchain
- Examples: a store of value, physical objects such as cars, services, shares in a company, a virtual pet

{{% note %}}

{{% /note %}}

---

### Tokens vs ETH

<img src="./../images/sbbs/eth_tokens.png" class="tokens"/>

{{% note %}}
Ether is the currency that runs the blockchain.
Tokens work similarly to Ether — you can store them in your wallet, send them to other addresses, etc. — but the difference is that a token doesn’t have its own blockchain. Tokens make use of existing blockchains and are usually developed for a specific application. 
{{% /note %}}

---

### Types of Tokens

---

### Fungibile Tokens

Tokens that are fungibile are equivalent and interchangeable

![](./../images/dappladies/dollar.jpg)

{{% note %}}
Fungible goods are equivalent and interchangeable, like Ether, fiat currencies, and voting rights.
{{% /note %}}

---

### Nonfungible Tokens

- Tokens that are non-fungible are tokens that contain a unique characteristics
- No 2 tokens are the same

![](./../images/dappladies/cryptokitty.png)

{{% note %}}
In a nutshell, when dealing with non-fungibles (like your house) you care about which ones you have, while in fungible assets (like your bank account statement) what matters is how much you have.
{{% /note %}}

---

### How do you make a token?

---

![](./../images/dappladies/smart-contract.jpg)

---

### Smart Contracts

- applications that can be deployed on a blockchain
- written in high level languages like Solidity
- compiled into EVM bytecode

{{% note %}}
- object oriented programming language used to write smart contracts
- influenced by C++, Python and Javascript
- easy to learn for programmers
{{% /note %}}

---

### Smart Contracts
- Solidity's code is encapsulated in contracts
- all variables and functions belong to a contract
- State variables are permanently stored in contract storage

```
pragma solidity ^0.5.0;

contract MyContract {
  uint256 value = 100;

  struct Person {
      uint age;
      string name;
      bool verified;
    }

  address public user;
  address public smartContract;
  
  bool exists;

}
```

---

### Smart Contracts: Mappings

- A way of storing organized data in Solidity
- A mapping is essentially a key-value store for storing and looking up data

```
contract MyContract {

  // For a financial app, storing a uint that holds the user's account balance:
  mapping (address => uint) public accountBalance;
  
  // store / lookup usernames based on userId
  mapping (uint => string) public userIdToName;

  // store / lookup to see if an address has voted
  mapping (address => bool) public voted;

}
```

---

### Token Contracts

- A token contract is simply a smart contract
- Sending tokens actually means “calling a function on a smart contract that someone wrote and deployed”
- Token contracts have mappings that map user addresses to their balance

`[user address] => balance`

{{% note %}}
It is these balances that represent the tokens themselves. Someone "has tokens" when their balance in the token contract is non-zero. That’s it! 
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

### ERC20

- ERC20.sol
- ERC20Burnable.sol
- ERC20Capped.sol
- ERC20Detailed.sol
- ERC20Mintable.sol
- ERC20Pausable.sol

https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token/ERC20

{{% note %}}
- Core: ERC20, - ERC20Detailed.sol
- designation of addresses that can create token supply ({ERC20Mintable})
- optional maximum cap ({ERC20Capped}), destruction of own tokens ({ERC20Burnable})
- designation of addresses that can pause token operations for all users ({ERC20Pausable}).
{{% /note %}}

---

### ERC20

```
function totalSupply() external view returns (uint256);

function balanceOf(address account) external view returns (uint256);

function transfer(address recipient, uint256 amount) external returns (bool);

function allowance(address owner, address spender) external view returns (uint256);

function approve(address spender, uint256 amount) external returns (bool);

function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);

```

{{% note %}}
balanceOf- returns token balance of account
transfer- Moves amount tokens from the caller’s account to recipient.
allowance- Returns the remaining number of tokens that spender will be allowed to spend on behalf of owner through transferFrom. This is zero by default.
approve- Sets amount as the allowance of spender over the caller’s tokens.
transferFrom- Moves amount tokens from sender to recipient using the allowance mechanism. amount is then deducted from the caller’s allowance.
{{% /note %}}

---

### ERC20

```
contract ERC20 {
    mapping (address => uint256) private _balances;
    mapping (address => mapping (address => uint256)) private _allowances;
    uint256 private _totalSupply;

    function totalSupply() public view returns (uint256) {
        return _totalSupply;
    }

    function balanceOf(address account) public view returns (uint256) {
        return _balances[account];
    }

    function _transfer(address sender, address recipient, uint256 amount) internal {
        require(sender != address(0), "ERC20: transfer from the zero address");
        require(recipient != address(0), "ERC20: transfer to the zero address");

        _balances[sender] = _balances[sender].sub(amount, "ERC20: transfer amount exceeds balance");
        _balances[recipient] = _balances[recipient].add(amount);
        emit Transfer(sender, recipient, amount);
    }

    function _mint(address account, uint256 amount) internal {
        require(account != address(0), "ERC20: mint to the zero address");

        _totalSupply = _totalSupply.add(amount);
        _balances[account] = _balances[account].add(amount);
        emit Transfer(address(0), account, amount);
    }

    function _burn(address account, uint256 value) internal {
        require(account != address(0), "ERC20: burn from the zero address");

        _balances[account] = _balances[account].sub(value, "ERC20: burn amount exceeds balance");
        _totalSupply = _totalSupply.sub(value);
        emit Transfer(account, address(0), value);
    }
}
```

---

### ERC721

- ERC721.sol
- ERC721Burnable.sol
- ERC721Enumerable.sol
- ERC721Full.sol
- ERC721Holder.sol
- ERC721Metadata.sol
- ERC721MetadataMintable.sol
- ERC721Mintable.sol
- ERC721Pausable.sol

https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token/ERC721

{{% note %}}
The EIP consists of three interfaces, found here as {IERC721}, {IERC721Metadata}, and {IERC721Enumerable}. Only the first one is required in a contract to be ERC721 compliant.
Additionally, {IERC721Receiver} can be used to prevent tokens from becoming forever locked in contracts. Imagine sending an in-game item to an exchange address that can’t send it back!. When using safeTransferFrom, the token contract checks to see that the receiver is an {IERC721Receiver}, which implies that it knows how to handle {ERC721} tokens
{{% /note %}}

---

### ERC721

```
function balanceOf(address owner) public view returns (uint256 balance);

function ownerOf(uint256 tokenId) public view returns (address owner);

function safeTransferFrom(address from, address to, uint256 tokenId) public;

function transferFrom(address from, address to, uint256 tokenId) public;

function approve(address to, uint256 tokenId) public;

function getApproved(uint256 tokenId) public view returns (address operator);

function setApprovalForAll(address operator, bool _approved) public;

function isApprovedForAll(address owner, address operator) public view returns (bool);

function safeTransferFrom(address from, address to, uint256 tokenId, bytes memory data) public;

```

{{% note %}}
Another big difference is safeTransferFrom, which is a safety measure of the ERC-721 standard, more specifically, the ERC721TokenReceiver interface. It checks if the target address is a smart contract and will throw an error if it isnt and the transaction will be reverted. This prevents anyone from accidentally sending their NFTs to a smart contract that doesn’t support them.
{{% /note %}}

---

### ERC721

```
contract ERC721 {
    mapping (uint256 => address) private _tokenOwner;
    mapping (uint256 => address) private _tokenApprovals;
    mapping (address => Counters.Counter) private _ownedTokensCount;
    mapping (address => mapping (address => bool)) private _operatorApprovals;

    function balanceOf(address owner) public view returns (uint256) {
        require(owner != address(0), "ERC721: balance query for the zero address");
        return _ownedTokensCount[owner].current();
    }

    function ownerOf(uint256 tokenId) public view returns (address) {
        address owner = _tokenOwner[tokenId];
        require(owner != address(0), "ERC721: owner query for nonexistent token");
        return owner;
    }

    function _mint(address to, uint256 tokenId) internal {
        require(to != address(0), "ERC721: mint to the zero address");
        require(!_exists(tokenId), "ERC721: token already minted");
        _tokenOwner[tokenId] = to;
        _ownedTokensCount[to].increment();
        emit Transfer(address(0), to, tokenId);
    }

    function _transferFrom(address from, address to, uint256 tokenId) internal {
        require(ownerOf(tokenId) == from, "ERC721: transfer of token that is not own");
        require(to != address(0), "ERC721: transfer to the zero address");
        _clearApproval(tokenId);
        _ownedTokensCount[from].decrement();
        _ownedTokensCount[to].increment();
        _tokenOwner[tokenId] = to;
        emit Transfer(from, to, tokenId);
    }
}
```
---

### Exercise - Tools
- The Truffle Suite
  - Truffle CLI
  - Ganache
  - Drizzle

`npm install -g truffle`

![](./../images/trufflesuite.png)

{{% note %}}
- Truffle is written in Node.js
- a CLI that dramatically reduces the complexity of building DApps
- ganache- creates a local ethereum network for development, testing
- drizzle - react.js library for building web UIs for DApps
{{% /note %}}

---

### Exercise - Build your own token
- Create and enter your project directory

```
mkdir token_workshop
cd token_workshop
```

- Tell truffle to initialize the project directory

```
truffle init
```

- Install Openzeppelin contracts

```
npm init
npm install @openzeppelin/contracts
```
---

### Exercise - Create Contracts
- create contract for our ERC20 token and ERC721 token

```
truffle create contract WWCToken
truffle create contract GameToken
```
---

### Exercise - Add ERC20 code

```
pragma solidity ^0.5.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/ERC20Detailed.sol";

contract WWCToken is ERC20, ERC20Detailed {
  constructor(uint256 initialSupply) ERC20Detailed("WWCToken", "WWC", 18 ) public {
    _mint(msg.sender, initialSupply);
  }
}

```

{{% note %}}
OpenZeppelin contracts are often used via inheritance, and here we’re reusing ERC20 for the basic standard implementation and ERC20Detailed to get the name, symbol, and decimals properties. Additionally, we’re creating an initialSupply of tokens, which will be assigned to the address that deploys the contract.
{{% /note %}}

---

### Exercise - Add Migrations file
- add a file called 2_deploy_contracts.js in the migrations directory

```
const WWCToken = artifacts.require("WWCToken");

module.exports = function(deployer) {
  deployer.deploy(WWCToken, 1000);
};

```

{{% note %}}

{{% /note %}}

---

### Exercise - Compile, Deploy, Interact

```
truffle compile
truffle develop
```
```
truffle(develop)> migrate
truffle(develop)> let instance = await WWCToken.deployed()
truffle(develop)> instance
truffle(develop)> let supply = await instance.totalSupply()
truffle(develop)> supply.toNumber()
truffle(develop)> let balance = await instance.balanceOf(accounts[0])
truffle(develop)> balance.toNumber()
 
```

{{% note %}}
truffle(develop)> instance.name()
truffle(develop)> instance.symbol()
truffle(develop)> instance.decimals()
{{% /note %}}

---

### Exercise - Send Tokens

Transfer function:

```
function transfer(address recipient, uint256 amount) public returns (bool) {
    _transfer(_msgSender(), recipient, amount);
    return true;
}
 
```

```
truffle(develop)> instance.transfer(accounts[1], 10, {from: accounts[0]})
truffle(develop)> balance = await instance.balanceOf(accounts[0])
truffle(develop)> balance.toNumber()
truffle(develop)> let otherBalance = await instance.balanceOf(accounts[1])
truffle(develop)> otherBalance.toNumber()
 
```
---

### Exercise - Add ERC721 code

```
pragma solidity ^0.5.0;

import "@openzeppelin/contracts/token/ERC721/ERC721Full.sol";
import "@openzeppelin/contracts/drafts/Counters.sol";

contract GameToken is ERC721Full {
    using Counters for Counters.Counter;
    Counters.Counter private _tokenIds;

    constructor() ERC721Full("GameToken", "GMT") public {
    }

    function createToken(string memory tokenURI) public returns (uint256) {
        _tokenIds.increment();

        uint256 tokenId = _tokenIds.current();
        _mint(msg.sender, tokenId);
        _setTokenURI(tokenId, tokenURI);

        return tokenId;
    }
}

```

{{% note %}}

{{% /note %}}

---

### Exercise - Migrations file
- add contract to migrations file

```
const WWCToken = artifacts.require("WWCToken");
const GameToken = artifacts.require("GameToken");

module.exports = function(deployer) {
  deployer.deploy(WWCToken, 1000);
  deployer.deploy(GameToken);
};

```

{{% note %}}

{{% /note %}}

---

### Exercise - Compile, Deploy, Interact

```
truffle compile
truffle develop
```
```
truffle(develop)> migrate
truffle(develop)> let instance = await GameToken.deployed()
truffle(develop)> instance
truffle(develop)> await instance.createToken("https://url.jpg")
truffle(develop)> instance.ownerOf(1)
truffle(develop)> web3.eth.getAccounts()
truffle(develop)> instance.tokenURI(1)
truffle(develop)> await instance.createToken("https://url.jpg", {from: accounts[1]})
 
```

{{% note %}}

{{% /note %}}

---

<section data-noprocess>
<style>
.hey {
  text-align: left;
}
i {
  padding: 10px;
}
</style>
<h2>Thank you :)</h2>

<div class="hey">
  <i class="fab fa-instagram"></i> <a href="https://twitter.com/devgirlla" target ="_blank">@devgirlla</a> <a href="https://twitter.com/dappladies" target ="_blank">@dappladies</a>
  </br>

  <i class="fab fa-twitter"></i> <a href="https://www.instagram.com/devgirlla/" target ="_blank">@devgirlla</a> <a href="https://www.instagram.com/dappladies/" target ="_blank">@dappladies</a>
    </br>

  <i class="fab fa-linkedin-in"></i> <a href="https://www.linkedin.com/in/kseniya-lifanova-aa50b19/" target ="_blank">@kseniya-lifanova</a> 
    </br>

  <i class="fas fa-desktop"></i> <a href="https://www.upstateinteractive.com" target ="_blank">www.upstateinteractive.com</a>
    </br>

  <i class="fas fa-desktop"></i> <a href="https://www.dappladies.com" target ="_blank">www.dappladies.com</a>
</div>
</section>

---

### Sources
- https://blockgeeks.com/guides/ethereum-token/
- https://docs.openzeppelin.com/contracts/2.x/tokens




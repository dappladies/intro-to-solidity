--- 
draft: false
title:  "Intro To Tokens"
outputs: ["Reveal"]
---

# Welcome!
Solidity Workshop: Intro to Tokens

![](./../images/solidity.png)

---

## Our Sponsor

![](./../images/dappladies/spring logo dark_new.png)

Thank you to Springlabs for sponsoring our event this evening!

{{% note %}}
- Spring Labs is building a protocol which allows participants such as financial institutions and consumers to share information such as credit and indentity data wihtout need to share the underlying data itself. They are an LA based company.
{{% /note %}}


---

### Tokens

- What is Eth?
- What are Tokens?
- ERC20 vs ERC721
- How do you create a token?

---

### Review: Ethereum

![](./../images/EVM.png)

---

### Review: Ethereum
- A network of nodes (computers) that are connected to one another
- Ethereum Virtual Machine (EVM)
- All transactions that happen are recorded and updated on all of the nodes

---

### Review: Smart Contracts
![](./../images/dappladies/smart-contract.jpg)

---

### Review: Smart Contracts

- applications, written in Solidity, that can be deployed on the Ethereum blockchain
- every function in a smart contract is a transaction that gets recorded and updated by the network

---

### Ether

- Ether is the currency that runs Ethereum 
- Since every function in a smart contract is a transaction or a complex computation that the Ethereum nodes need to process, there is a cost: "gas"
- Gas is paid in Ether
- Miners are incentivized to process transactions for the Ethereum network because they are compenstated in Eth

{{% note %}}
Native tokens that form part of the core of the blockchain. Ethereum would not function without ETH. 
{{% /note %}}

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
Core: ERC20, - ERC20Detailed.sol
Multiple: designation of addresses that can create token supply ({ERC20Mintable}), with an optional maximum cap ({ERC20Capped}), destruction of own tokens ({ERC20Burnable}), designation of addresses that can pause token operations for all users ({ERC20Pausable}).
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

### Other Token Standards: ERC777
- a standard for fungible tokens that is focused on allowing more complex interations when trading tokens
- its killer feature are receive hooks
- A hook is simply a function in a contract that is called when tokens are sent to it, meaning accounts and contracts can react to receiving tokens.

---

### Other Token Standards: ERC1155
- a standard for managing multiple token types
- a single deployed contract may inclue any combination of fungible tokens, non-fungible tokens or other configurations

---

### Let's Code!

---

### Sources
- https://blockgeeks.com/guides/ethereum-token/
- https://docs.openzeppelin.com/contracts/2.x/tokens




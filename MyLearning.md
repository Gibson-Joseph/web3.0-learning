# My Learning:

```javascript
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

contract Will {
    bool deceased;
    address onwer;
    uint256 fortune;

    // The public keyword is enable the visibility
    // payable is allowing the function to send and recieve ether
    constructor() payable {
        onwer = msg.sender;
        fortune = msg.value;
        deceased = false;
    }

    // Modifiers
    // modifiers are add ons for our function that can create additional logic for them.

    modifier onlyOwner() {
        require(msg.sender == onwer);
        _; // the underscore just tells the function to continue.
    }

    modifier mustBeDeceased() {
        require(deceased == true);
        _;
    }

    // list of familly wallet
    address payable[] familyWallets; //not understatn why we use payable

    // mapping throug the inheritance
    mapping(address => uint256) inheritance;

    // Set inheriance for each address
    function setInheritance(
        address payable wallet,
        uint256 amount // Only onwer can run that
    ) public onlyOwner {
        familyWallets.push(wallet);
        inheritance[wallet] = amount;
    }

    // pay each family member based on their wallet address

    function payout() private mustBeDeceased {
        for (uint256 i = 0; i < familyWallets.length; i++) {
            // Funds from a contract address to receive her address, and it does it pulling through the familly wallets
            familyWallets[i].transfer(inheritance[familyWallets[i]]);
        }
    }

    // Oracle switce similation
    function hasDeceased() public onlyOwner {
        deceased = true;
        payout();
    }
}

```

# Solidity Address Variable Type:

The Address type that hold the 20 byte value representing the size of an Ethereum adress.

# Mapping:

A mapping holds a reference to a value.

syntax

```javascript
mapping(_keyType => _valueType)

mapping(address => uint) public balance
```

# Modifier:

Modifier allow control to the behavior of a function

# Constructor:

A Constructor is an optional function declared with the constructor keyword which is executed only upon contract creation. Constructor functions can be either puplic or internal.

# BlockChain Tranction:

link: https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/27756522#overview

BlockChain is a database, but it is globaly shared. It is a decentralized database.

If you want to change something in database, then what you create you have to do is create transcations and these tranction have to be accepted by everybody participating.

# Destructuring and Multiple returns from functions in solidity:

https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/34653504#overview

# Crypto Token Contract SetUp:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/27756528?start=0#overview
contract Coin {
    // the keyword public it's making the variables
    // here accessible from other contracts

    address public minter;
    mapping(address => uint256) public balances;

    // Event to allow clients to react to specific  contract changes you declare
    event Sent(address from, address to, uint256 amount); // not understan in event

    // constructor code is only run when we deploy contract
    constructor() {
        minter = msg.sender;
    }

    //make a new coin and send them to an address
    // only the owner can sen these coins
    function mint(address receiver, uint256 amount) public {
        require(msg.sender == minter);
        balances[receiver] += amount; // not understand
    }

    // Send any amount of coins
    // to an existing address

    error insufficientBalance(uint256 requested, uint256 available);

    function sent(address receiver, uint256 amount) public {
        // require amount to be greater then x = true and then run this -
        if (amount > balances[msg.sender])
            revert insufficientBalance({
                requested: amount,
                available: balances[msg.sender]
            }); // revert will actually stop the this transaction from happining and provide the information regrading the transaction

        balances[msg.sender] -= amount;
        balances[receiver] += amount;
        emit Sent(msg.sender, receiver, amount); // not understand
    }
}

```

# KryptoBirdz

https://01clarian.github.io/KryptoBirdz/
https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/28491558#overview

# NFT

Non-Fungible Token (NFT)

# How BlockChain Works:

https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/27756568#overview

# What is crypto mining:

https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/27756576#overview

# Proof of work & Proof of stake

ethereum is proof of stake.
bitcoin is proof of work.

# Install ganache

https://www.udemy.com/course/complete-dapp-solidity-react-blockchain-development/learn/lecture/27756602#overview

https://trufflesuite.com/ganache/

```
$ chmod a+x ganache-2.5.4-linux-x86_64.AppImage
$ ./ganache-2.5.4-linux-x86_64.AppImage --appimage-extract
```

https://dapp-world.com/blogs/01/how-to-connect-ganache-with-metamask-and-deploy-smart-contracts-on-remix-without-1619847868947#:~:text=then%20Chain%20ID%20for%20ganache,currency%20symbol%20as%20%22ETH%22.

# 1_initial_migration.js

In Root foilder create migrations folder that contain this js file

```javascript
const Migrations = artifacts.require("Migrations");

module.exports = function (deployer) {
  deployer.deploy(Migrations);
};
```

# 2_deploy_contracts.js

In Root foilder create migrations folder that contain this js file

```javascript
const Tether = artifacts.require("Tether");
const RWD = artifacts.require("RWD");
const DecentralBank = artifacts.require("DecentralBank");

module.exports = async function (deployer) {
  // Deploy Gibson Tether Contract
  await deployer.deploy(Tether);

  // Deploy RWD Contract
  await deployer.deploy(RWD);

  // Deploy DecentralBank Contract
  await deployer.deploy(DecentralBank);
};
```

# truffle-config.js

this file in our root folder

```javascript
require("babel-register");
require("babel-polyfill");

module.exports = {
  networks: {
    development: {
      host: "127.0.0.1",
      port: "7545",
      network_id: "*", // match to any network
    },
  },
  contracts_directory: "./src/contracts/",
  contracts_build_directory: "./src/truffle_abis",
  compilers: {
    solc: {
      version: "^0.5.0",
      optimizer: {
        enabled: true,
        runs: 200,
      },
    },
  },
};
```
# truffle_abis (folder)

In Root foilder create truffle_abis folder. This folder in src folder

# package.json

```javascript
"dependencies": {
    "@types/jest": "^26.0.24",
    "@types/node": "^16.3.1",
    "@types/react": "^17.0.14",
    "@types/react-dom": "^17.0.9",
    "babel-polyfill": "6.26.0",
    "babel-preset-env": "1.7.0",
    "babel-preset-es2015": "6.24.1",
    "babel-preset-stage-2": "6.24.1",
    "babel-preset-stage-3": "6.24.1",
    "babel-register": "6.26.0",
    "bootstrap": "4.3.1",
    "chai": "4.2.0",
    "chai-as-promised": "7.1.1",
    "chai-bignumber": "3.0.0",
    "identicon.js": "^2.3.3",
    "react": "^16.8.4",
    "react-bootstrap": "1.0.0-beta.5",
    "react-dom": "16.8.4",
    "react-particles-js": "^3.5.3",
    "react-scripts": "2.1.3",
    "react-tsparticles": "^1.31.2",
    "solc": "^0.8.6",
    "truffle": "^5.1.39",
    "typescript": "^4.3.5",
    "web3": "1.2.11"
  },
```
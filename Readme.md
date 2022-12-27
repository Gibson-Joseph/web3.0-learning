# Web 3.0

## SHA256 Hash?

### Hash:

Hash is unique fixed length string to identify a piece of data.

## Hash Algorithm :

A function that computes data into a unique hash

## Mining:

The process of finding the "solution" to the blockchain "problem".

in our example, the "problem" was to find a hash that starts with four zeros.

Nodes get paid for mining blocks.

## Block:

A list of transactions mined together.

## Decentralized:

Having no single point of authority

## Nonce:

A "Number used once" to find the "solution" to the blockchain problem.

It's also used to define the transaction number for an account/address.

# Signing Transactions:

A "one way" process. Someone with a private key signs a transaction by their private key being hashed with their transaction with their transaction data.

Anyone can then verify this new transaction hash with your public key.

## Private Key:

Only Known to the key holder, it's used to "sign" transactions.

## Public Key:

We want everybody to have access.

Public key is derived from your private key. Anyone can "see" it, and use it to verify that a transaction came from you.

Private Key > Public Key > address

## Elliptic Curive Digital Signature Algorithm:

## Gas 2: Block Rewards & EIP 1559

It's not important to understand everything.
---could not understand "gas" please rafer more.---
video : 1:30:00

------------------------- doubt -------------
Transaction Fee?
Gas price ?
Gas Limit & Usage by Txn:

# Gas Fees?

Gas fees are paid by whoever makes the transaction.
Burnt & Txn Saving Fees?
Gwei?

---

Check Gas Fee and more using below link:
https://eth-converter.com/

# High-Level Blockchain Fundamentals:

## node:

A single instance in decentralized network.

Blockchain nodes keep lists of the transaction that occur.
Blockchain is a decentralized database.

# Consensus:

Consensus is the mechanism used to agree on the state of a blockchain.

1. Chain Selection algorithm.
   2.sybil resistance mechanism.

-----doubt-----

# proof of work

proof of work network is called miners

# proof of stake

proof of stake network is called validators.

proof of stake is a cryptocurrency consensus mechanism for processing transcation and creating new blocks in a blockchain.

PoS uses much less energy

---

---

please refer the heading (important)

# Proof of work:(PoW)

Proof of work is a piece of the overall Consensus protocall, which in Bitcoin and etherium.

Proof of work uses a lot of energy

This has recently changed as of EIP 1559

pow is costs a lot of electricity, because every single node is running as fast as they can to win this race to get the rewards.

# Nakamoto Consensus

Nakamoto Consensus is combination of proof of works, and this is longast chain rule

# block Confirmations

# Two type of attacks?

1. Sybil attack
   Sybil attack is a user creates a whole bunch of pseudo anonymous accounts to try to influence a network.
2. 51% Attack
   ?

---

# validators

# Randomness

# Scalability

# sharding

# Rollups

---

ETH and BTC are proof of work
ETH 2.0 will be Proof of Stake.
PoW & PoS are sybil resistance mechanisms

Consensus is how blockchains decide what the state of the chain is

Shardings and rollups are scalabilityb solutions.

---

# Solidity Types:

booleanS
unit
int
address
bytes

# boolean

define some type of true false,

# unit

unsigned integer, which means it's going to be a whole number that is not positive or negative.

# int

positive or negative number

# address

which is going to be an address of metaMask.

---

please refer Bits vs Bytes video:2:14:26

# functions:

"Functions" or "Methods" execute a subset of code when called.

# small solidity example:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.8; // 0.8.12

// contract is a keyword in solidity
// contract is similar to a class in any object oriented programming like javascript

// Every smart contracts have address just like our wallet account do
contract SimpleStorage {
//everything inside the open and close curly brackets is going to be the content of this contract.

//Types below: --> check solidity docs
//boolean, uint, int, address, bytes

// default value is zero in solidity <-- check docs
    // bool hasFavoriteNumer= true;
    uint256 public favoriteNumer;

// puplic variable implicitly get assigned a function that returns its value!
// the default visibility is internal

    // string favoriteText = "Gibson";
    // int256 favoriteInt = -5;
    // address myAddress = 0x846781d48EE9231Fa0EA0b0C0855f711C2fE88d2;
    // bytes32 favoriteBytes = "cat";

    function store(uint256 _favoriteNumer) public {
        favoriteNumer = _favoriteNumer;
        // retrive();
    }

// view function
    function retrive() public view returns(uint256){
        return favoriteNumer;
    //view and pure functions, when called alone, don't spend gas
    // view and pure function disallow modification of state
    // Pure functions additionally disallow you to read from blockchain state.
    }
//pure function
    function add() public pure returns (uint256){
        return ( 1+1);
    }

}
//0xd9145CCE52D386f254917e481eB44e9943F39138

//Any time you change something on-chain, including making a new contract, it happens in a transaction

```

---

# basic solidity Arrays & Structs:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.8; // 0.8.12

contract SimpleStorage {

    uint256 public favoriteNumer;
    uint256 public brothersFavoriteNumer;
    uint256 public sistersFavoriteNumer;

    Pepole public person =Pepole({
        favoriteNumer:1,
        name:"Gibson"
        //in output showing 0 and 1 is index
    });

       Pepole public person1 =Pepole({
        favoriteNumer:3,
        name:"joseph"
    });

    struct Pepole {
        uint256 favoriteNumer;
        string name;
    }

    function store(uint256 _favoriteNumer) public {
        favoriteNumer = _favoriteNumer;
    }

    function retrive() public view returns(uint256){
        return favoriteNumer;
    }

    function add() public pure returns (uint256){
        return ( 1+1);
    }

}

```

# struct :

allows you to create more complicated data types that have multiple properties.

# Array in solidity:

An Array is a data structure that holds a list of other types.

# Dynamic Array Vs Fixed-Sized Array:

## Dynamic Array

Size of the array is given add.

## Fixed-Sized Array

?

# Basic Solidity Memory, Storage & calldata :

// check above heading

# EVM Overview:

EVM can access and store information in six place

1. Stack
2. Memory --
3. Storage --
4. Calldata --
5. Code
6. Logs

# calldata

calldata is a temporary variable that can't be modified

# Memory:

Memory is a temporary variable that can be modified.

# Storage:

Storage is permanent variable that can be modified.

```javascript
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.8; // 0.8.12

contract SimpleStorage {
        uint256 favoriteNumer; //this is storage (type) in by default
        // i given type storage, it will throw the error.
    struct People {
        uint256 favoriteNumer;
        string name;
    }
    // uint256[] public favoriteNumerList; //<- similar to array
    People[] public people; //our array is currently empty
    function store(uint256 _favoriteNumer) public {
        favoriteNumer = _favoriteNumer;
    }
    function addPerson(string memory _name, uint256 _favoriteNumer) public {
        // People memory newPerson = People({
        //     favoriteNumer:_favoriteNumer,
        //     name:_name   //<-- need memory keyword
        // });
        // _name="cat"; //change
    people.push(People(_favoriteNumer,_name)); //<-- no need memory
    }
}
```

# Basic solidity Mappings:

A mapping is called is a data structure where a key is "mapped" to a single value.

# Deploying your first COntract

---

# Remix Storage Factory

Single file can hold multiple contract file
import in top of the file

# Intracting with other contracts

---

# Inheritance & Overrides :

Inherete one contract to anothor contract

# override (override the functions)

1. virtual
2. override

---

# Lesson 4

# Remix Fund Me

# Sending ETH Through A function & Reverts (3:34:12)

# What is reverting?

# example:

```javascript
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Get funds from users
// Withdraw funds
// Set a minimum funding value in USD

contract FundMe {
    uint256 public number;
    function fund() public payable{
        number=5;
        //Want to be able to set a minimum fund amount in USD
        // 1. How do we send ETH to this contract?
       require (msg.value > 1e18,"Didn't send enough!"); // 1e18 == 1 * 10 ** 18 === 1000000000000000000
       //require keyword is a checker

       //What is reverting?
            //the condition is faled any value is revert.
       //undo any action before, and send remaining gas back
    }
}
```

# ChainLink & Oracles: (3:44:00)

# Deterministic

# Non-deterministic

# The Oracle Problem:

Smart Contracts are unable to connect with external systems, data feeds, APIs, existing payment systems or any other off chain resources on their own.

# The smart contract connectivity problem

Blockchin Oracle : Any davice that intracts with the off-chain world to provide external data or computation to smart contracts.

# Chainlink Data Feeds

Powering over $50 billion in the Defi world

# Chainlink VRF :

Securing Randomness for your applications.

# Chainlink Keepers :

Decentralized Event-Driven Execution.

# End-to-end Reliability is the Promise of the Smart Contracts:

# Connect to any APT:

YT (3:56:00)
link : https://www.youtube.com/watch?v=gyMwXuJrbJQ

# Interfaces & Price Feeds

yt: 4:04:00

```javascript
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Get funds from users
// Withdraw funds
// Set a minimum funding value in USD

interface AggregatorV3Interface {
  function decimals() external view returns (uint8);

  function description() external view returns (string memory);

  function version() external view returns (uint256);

  function getRoundData(uint80 _roundId)
    external
    view
    returns (
      uint80 roundId,
      int256 answer,
      uint256 startedAt,
      uint256 updatedAt,
      uint80 answeredInRound
    );

  function latestRoundData()
    external
    view
    returns (
      uint80 roundId,
      int256 answer,
      uint256 startedAt,
      uint256 updatedAt,
      uint80 answeredInRound
    );
}

contract FundMe {

    uint256 public minimumUsd = 50;

    function fund() public payable{
        //Want to be able to set a minimum fund amount in USD
        // 1. How do we send ETH to this contract?
       require (msg.value > minimumUsd,"Didn't send enough!"); // 1e18 == 1 * 10 ** 18 === 1000000000000000000
       //require keyword is a checker
    }
       function getPrice() public {
           // ABI
           // Address 0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e (in docs)
       }

       function getVersion() public view returns (uint256){
           AggregatorV3Interface priceFeed = AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
           return priceFeed.version();
       }

       function getConversionRate() public {}

    // function withdraw() public {}
}
```

```javascript
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// you can import file local and github
// import "./AggregatorV3Interface.sol"; //local
import "https://github.com/smartcontractkit/chainlink/blob/develop/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol"; //github

contract FundMe {

    uint256 public minimumUsd = 50;

    function fund() public payable{
       require (msg.value > minimumUsd,"Didn't send enough!"); // 1e18 == 1 * 10 ** 18 ===
    }
       function getPrice() public {
       }

       function getVersion() public view returns (uint256){
           AggregatorV3Interface priceFeed = AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
           return priceFeed.version();
       }

       function getConversionRate() public {}

    // function withdraw() public {}
}
```

# Floating Point Math in Solidity:

yt: <= 4:21:58

```javascript
//SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// you can import file local and github
import "./AggregatorV3Interface.sol"; //local
contract FundMe {

    uint256 public minimumUsd = 50 * 1e18; //1 * 10 ** 18

    function fund() public payable{
        //Want to be able to set a minimum fund amount in USD
        // 1. How do we send ETH to this contract?
       require (getConversionRate(msg.value) >= minimumUsd,"Didn't send enough!"); // 1e18 == 1 * 10 ** 18 === 1000000000000000000
       // 18 decimals
       //require keyword is a checker
    }
       function getPrice() public view returns(uint256) {
           AggregatorV3Interface priceFeed= AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
            (,int256 price,,,)=priceFeed.latestRoundData();
            // ETH in terms of USD
            return uint256(price * 1e10); // 1**10 == 10000000000
       }

       function getVersion() public view returns (uint256){
           AggregatorV3Interface priceFeed = AggregatorV3Interface(0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e);
           return priceFeed.version();
       }

       function getConversionRate(uint256 ethAmount) public view returns(uint256) {
           uint256 ethPrice = getPrice();
           uint256 ethAmountInUSD = (ethPrice * ethAmount) / 1e18;
           return ethAmountInUSD;
       }

    // function withdraw() public {}
}
```

---
# Basic SOlidity Arrays & Structs 2
yt: < 4:25:02
# Libraries 
yt: 4:25:02 

```javascript
// SPDX-License-Identifier: MIT

pragma solidity ^0.8.0;

import "./AggregatorV3Interface.sol";
// import "https://github.com/smartcontractkit/chainlink/blob/develop/contracts/src/v0.8/interfaces/AggregatorV3Interface.sol"; //github

// use library
//library can have any state variable
// All the function into the library
// this should be a internal
library PriceConverter {
    function getPrice() internal view returns (uint256) {
        AggregatorV3Interface priceFeed = AggregatorV3Interface(
            0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e
        );
        (, int256 price, , , ) = priceFeed.latestRoundData();
        // ETH in terms of USD
        return uint256(price * 1e10); // 1**10 == 10000000000
    }

    function getVersion() internal view returns (uint256) {
        AggregatorV3Interface priceFeed = AggregatorV3Interface(
            0xD4a33860578De61DBAbDc8BFdb98FD742fA7028e
        );
        return priceFeed.version();
    }

    function getConversionRate(uint256 ethAmount)
        internal
        view
        returns (uint256)
    {
        uint256 ethPrice = getPrice();
        uint256 ethAmountInUSD = (ethPrice * ethAmount) / 1e18;
        return ethAmountInUSD;
    }
}

```
# SafeMath, OverFlow Checking, and the "unchecked" keyword:  
YT: 4:29:54

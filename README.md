# ETH-AVAX-PROOF-Intermediate-EVM-Course
# Project Title
write a smart contract that implements the require(), assert() and revert() statements.
## Description

This is a simple project for simulating the development of smart contracts using Remix IDE and the Solidity language .Firstly We use the modifier and constructor. Then make deposit,withdraw,getbalance and totalbalance function.In this project we use the error handling concept.
so, We use the revert() , require() and assert() .

## Getting started
### Installing

* To run the project code, you need an IDE where you can run the Solidity language. One such IDE is the online Remix IDE (https://remix.ethereum.org/), which you can run on any browser of your choice.

* The code in this project can be used by simply copying it to the editor of any IDE where you can run Solidity version 0.8.7.

 ### Executing program

 * How to run the program:
1. Copy the Solidity code provided in the "project_1_AVAX" file.

2. Open Remix IDE (https://remix.ethereum.org/).

3. In the Remix IDE, create a new file and paste the copied code into it.

4. Compile the Code by either pressing "Ctrl + S" to compile the code or using the Compile button in the Remix IDE interface.

5. Use the Deploy button in the Remix IDE to deploy the contract to a local Ethereum network or a test network.

6. Use the deployed contract's interface in Remix IDE  and then deposit the ether and then input some ether in the deposit button and then call the deposit function and then call the getbalance and total balance.
   
. CODE

```

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

contract myContract {
    mapping(address => uint256) private balances;
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    // Modifier to restrict access to the owner
    modifier onlyOwner() {
        require(msg.sender == owner, "You are not the owner");
        _;
    }

    // Function to deposit ether into the bank
    function deposit() public payable {
        require(msg.value > 0, "Deposit amount must be greater than zero");
        balances[msg.sender] += msg.value;
    }

    // Function to withdraw ether from the bank
    function withdraw(uint256 _amount) public {
        require(_amount <= balances[msg.sender], "Insufficient balance");
        balances[msg.sender] -= _amount;
        payable(msg.sender).transfer(_amount);
    }

    // Function to get the balance of the caller
    function getBalance() public view returns (uint256) {
        return balances[msg.sender];
    }

    // Function to check the total balance in the bank (only accessible by the owner)
    function totalBalance() public view onlyOwner returns (uint256) {
        uint256 total = address(this).balance;
        assert(total >= 0); // Assert that the total balance is non-negative
        return total;
    }

    // Function to revert a transaction
    function revertTransaction() public pure {
        revert("This transaction has been reverted");
    }
}
```

## Help

If you encounter any issues or have any questions, here are some common solutions:

1. Ensure you are using Solidity version 0.8.7 or later.
   
2. Check the Remix IDE console for error messages and follow the guidance provided.

 ## Authors

 Contributors names and contact info

 Ravi
 
 mail: ssiwach9036@gmail.com

 ## License

 This project is licensed under the [MIT] License - see the LICENSE.md file for details

 

  
  


## Project Title

Smart Contract: MyToken

## Description

This Solidity smart contract implements a simple token system with minting and burning capabilities. The contract allows for creating and destroying tokens while keeping track of token balances and total supply. 

## Getting Started

### Requirements

* Token Details: The contract has public variables to store details about the token, including its name, abbreviation, and total supply.
* Address Balances: The contract uses a mapping to associate addresses with their token balances (address => uint).
* Mint Function: The contract includes a 'mint' function that increases the total supply by a specified value and increments the balance of the sender's address by the same value.
* Burn Function: The contract has a 'burn' function that reduces the total supply and decreases the balance of the sender's address by a specified value.
* Balance Check: The 'burn' function includes conditional checks to ensure that the balance of the sender is greater than or equal to the amount intended to be burned.

### Contract Details

* tokenName: A public string variable storing the name of the token (e.g., "PLETHORA").
* abbrv: A public string variable holding the abbreviation of the token (e.g., "PL").
* totalSupply: A public uint variable representing the total supply of the token. It starts at 0 and increases with minting while decreasing with burning.
* balances: A mapping that associates addresses with their token balances.
```
// public variables
string public tokenName = "MXP";
    string public abbrv = "MX";
    uint public totalSupply = 0;
    
    //mapping variables
    mapping (address=> uint) public balances;
```

### Functions

* 'mint(address _address, uint _value)': A function for minting new tokens. It increases the total supply and the balance of the specified address.

* 'burn(address _address, uint _value)': A function for burning tokens. It decreases the total supply and the balance of the specified address, but only if the sender's balance is sufficient.
```
// mint() function
function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;  
}

//burn() function
function burn( address _address,uint _value) public {
        if( balances[_address] >= _value){
            totalSupply -= _value;
            balances[_address] -= _value;
        }
```

## Implementation

To use this contract, you can deploy it to an Ethereum blockchain using a development environment like Remix or Truffle. Here's a basic example of how to interact with the contract:

1. Deploy the contract.
2. Call the mint() function to create new tokens and allocate them to an address.
3. Call the burn() function to destroy a certain amount of tokens, provided that the sender has a sufficient balance.



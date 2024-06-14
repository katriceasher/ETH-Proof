# ETH-Proof
Final Project for ETH Proof Beginner Course
Overview
MyToken is a simple Ethereum smart contract that implements a basic ERC20-like token. This token, named META (symbol: MTA), includes functionalities to mint and burn tokens while keeping track of the total supply and individual balances.

Features
Public Variables:

tokenName: The name of the token (META).
symbol: The abbreviation of the token (MTA).
totalSupply: The total supply of tokens in circulation.
Balances Mapping:

Keeps track of the balance of each address.
Mint Function:

Increases the total supply and the balance of the specified address.
Burn Function:

Decreases the total supply and the balance of the specified address, ensuring the address has enough tokens to burn.
Contract Code
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    string public tokenName = "META";
    string public symbol = "MTA";
    uint public totalSupply = 0;
    
    mapping(address => uint) public balances;
    
    function mint(address _to, uint _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }
    
    function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Insufficient balance");
        
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
Functions
Mint
solidity
Copy code
function mint(address _to, uint _value) public

Description: Increases the totalSupply by _value and increases the balance of _to by _value.

Parameters:
_to: The address to which the tokens will be minted.
_value: The number of tokens to be minted.
Burn
solidity
Copy code
function burn(address _from, uint _value) public
Description: Decreases the totalSupply by _value and decreases the balance of _from by _value. Ensures that _from has enough balance to burn.
Parameters:
_from: The address from which the tokens will be burned.
_value: The number of tokens to be burned.

Usage
Deploy the Contract: Deploy the MyToken contract to the Ethereum network.
Mint Tokens: Use the mint function to create new tokens and assign them to a specific address.
Burn Tokens: Use the burn function to destroy tokens from a specific address, ensuring the address has sufficient balance.

License
This project is licensed under the MIT License.


# FinalTokenAssessment Contract

## Overview

The `FinalTokenAssessment` contract is a simple implementation of an ERC20-like token on the Ethereum blockchain. This contract allows for basic token operations such as minting and burning tokens, with public variables to store the token's details.

## Requirements

1. **Public Variables:**
    - `token_Name`: Stores the name of the token.
    - `token_Abbvr`: Stores the abbreviated symbol of the token.
    - `token_supply`: Stores the total supply of the token.
   
2. **Mapping:**
    - `balance`: A mapping from addresses to their token balances.

3. **Functions:**
    - `mintFunc`: Increases the total supply and the balance of a specified address.
    - `burnFunc`: Decreases the total supply and the balance of a specified address, with a check to ensure sufficient balance.

## Contract Details

### Public Variables

- `string public token_Name = "MY_TOKEN";`
    - The name of the token.
- `string public token_Abbvr = "MT";`
    - The abbreviated symbol of the token.
- `uint public token_supply = 0;`
    - The total supply of the token, initially set to 0.

### Mapping

- `mapping(address => uint) public balance;`
    - A mapping that associates each address with its token balance.

### Functions

#### mintFunc

```solidity
function mintFunc(address _ADDRESS, uint _VALUE) public {
    token_supply += _VALUE;
    balance[_ADDRESS] += _VALUE;
}
```

- **Description:** Mints new tokens by increasing the total supply and the balance of the specified address.
- **Parameters:**
    - `_ADDRESS`: The address to which the tokens will be minted.
    - `_VALUE`: The amount of tokens to be minted.

#### burnFunc

```solidity
function burnFunc(address _ADDRESS, uint _VALUE) public {
    if (balance[_ADDRESS] >= _VALUE) {
        token_supply -= _VALUE;
        balance[_ADDRESS] -= _VALUE;
    }
}
```

- **Description:** Burns tokens by decreasing the total supply and the balance of the specified address, provided the address has sufficient balance.
- **Parameters:**
    - `_ADDRESS`: The address from which the tokens will be burned.
    - `_VALUE`: The amount of tokens to be burned.
- **Condition:** Ensures that the address has a balance greater than or equal to the amount to be burned before performing the burn operation.

## Usage

### Deploying the Contract

1. **Compile the Contract:**
   - Ensure that your Solidity compiler version is `0.8.18`.
   - Compile the contract using Remix, Truffle, or Hardhat.

2. **Deploy the Contract:**
   - Deploy the contract to your desired Ethereum network (e.g., Mainnet, Ropsten, or a local testnet).

### Interacting with the Contract

1. **Minting Tokens:**
   - Call the `mintFunc` function with the address to mint to and the amount of tokens to mint.
   - Example: `mintFunc(0xYourAddress, 1000);`

2. **Burning Tokens:**
   - Call the `burnFunc` function with the address to burn from and the amount of tokens to burn.
   - Ensure the address has enough tokens to burn.
   - Example: `burnFunc(0xYourAddress, 500);`

## License

This contract is licensed under the MIT License.

# Project-Create-and-Mint-Token

## Description

I created my own ERC20 token and deployed it using HardHat or Remix. Users are able to burn and transfer tokens. The contract owner is able to mint tokens to a provided address.

### Executing program


```

//SPDX-License-Identifier: MIT
pragma solidity 0.8.13;

import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol";
import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol";

contract GeraldsToken is ERC20("Geralds Token", "GG"), Ownable {
    constructor() Ownable(msg.sender) {}

    function mint(address account, uint256 amount) public onlyOwner {
        _mint(account, amount);
    }

    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }

    function burn(uint256 amount) public {
        _burn(_msgSender(), amount);
    }
}



```


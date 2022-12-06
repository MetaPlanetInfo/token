# token
Depository for MPT Token Deployment
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.9;

import "@openzeppelin/contracts@4.8.0/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@4.8.0/token/ERC20/extensions/draft-ERC20Permit.sol";
import "@openzeppelin/contracts@4.8.0/token/ERC20/extensions/ERC20Votes.sol";

/// @custom:security-contact info@meta-planet.one
contract MetaPlanetToken is ERC20, ERC20Permit, ERC20Votes {
    constructor() ERC20("MetaPlanetToken", "MPT") ERC20Permit("MetaPlanetToken") {
        _mint(msg.sender, 300000000 * 10 ** decimals());
    }

    // The following functions are overrides required by Solidity.

    function _afterTokenTransfer(address from, address to, uint256 amount)
        internal
        override(ERC20, ERC20Votes)
    {
        super._afterTokenTransfer(from, to, amount);
    }

    function _mint(address to, uint256 amount)
        internal
        override(ERC20, ERC20Votes)
    {
        super._mint(to, amount);
    }

    function _burn(address account, uint256 amount)
        internal
        override(ERC20, ERC20Votes)
    {
        super._burn(account, amount);
    }
}

# Killable-contract
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract Killable {
    address public owner;

    constructor() {
        owner = msg.sender;
    }

    modifier onlyOwner() {
        require(msg.sender == owner);
        _;
    }

    function kill() external onlyOwner {
        selfdestruct(payable(owner));
    }

    receive() external payable {}
}

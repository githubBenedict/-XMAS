# -XMAS
<p> $XMAS token </p>
  <p> $XMAS token is an bep20 token with a total supply of 1,000,000 tokens.</p>
  <p> $XMAS token has a base website digitalmarketingbyben.com </p>
  <p> $XMAS token source code is available @ https://bscscan.com/address/0x83dca390e6b91ea82c55e9181c1d1b4fdc92a243#code#L1 </p>
  <p> $XMAS token is offering it's logo created by @benedictk3mp on airnft here (https://app.airnfts.com/nft/XMAS_1636396075925) </p>
  
  
  pragma solidity ^0.8.2;

contract Token {
    mapping(address => uint) public balances;
    mapping(address => mapping(address => uint)) public allowance;
    uint public totalSupply = 1000000 * 10 ** 18;
    string public name = "XMAS Day Coin";
    string public symbol = "XMAS";
    uint public decimals = 18;
    
    event Transfer(address indexed from, address indexed to, uint value);
    event Approval(address indexed owner, address indexed spender, uint value);
    
    constructor() {
        balances[msg.sender] = totalSupply;
    }
    
    function balanceOf(address owner) public returns(uint) {
        return balances[owner];
    }
    
    function transfer(address to, uint value) public returns(bool) {
        require(balanceOf(msg.sender) >= value, 'balance too low');
        balances[to] += value;
        balances[msg.sender] -= value;
       emit Transfer(msg.sender, to, value);
        return true;
    }
    
    function transferFrom(address from, address to, uint value) public returns(bool) {
        require(balanceOf(from) >= value, 'balance too low');
        require(allowance[from][msg.sender] >= value, 'allowance too low');
        balances[to] += value;
        balances[from] -= value;
        emit Transfer(from, to, value);
        return true;   
    }
    
    function approve(address spender, uint value) public returns (bool) {
        allowance[msg.sender][spender] = value;
        emit Approval(msg.sender, spender, value);
        return true;   
    }
}


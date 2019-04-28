# BuyTokens
In ico for buying the tokens
pragma solidity >=0.4.2;
import './SafeMath.sol';
import './ERC20.sol';
	contract ERC20Basic {
	  uint public totalSupply;
	  function balanceOf(address who) public view returns (uint);
	  function transfer(address to, uint value) public returns (bool);
	  event Transfer(address indexed from, address indexed to, uint value);
	}
contract BuyTokens is ERC20Basic,ERC20 {
    string public name = "Aditya";
    string public token = "first";
    uint public decimals = 18;
    uint prize = 100;
    uint public constant INITIAL_SUPPLY = 100000000 * 10**18;
    constructor() public {
	    totalSupply = INITIAL_SUPPLY;
	    _balances[msg.sender] = INITIAL_SUPPLY;
	  }
	  
	  function() payable external{
	      buytokens(msg.value,msg.sender);
	  }
	  
	  function buytokens(uint rxEth,address investor) public {
	   uint sendTokens =  prize * rxEth;
	   transfer(investor,sendTokens);
	   
	  }
}

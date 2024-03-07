# Question 1 
## The parameter X represents a function. Complete the function signature so that X is a standard ERC20 transfer function (other than the visibility) The query function should revert if the ERC20 function returns false.
```
function query(uint _amount, address _receiver, X) public { ... }
```

First let’s clarify that we know a signature for a standard ‘transfer function’. This could be used in an interface.
```
function transfer(address recipient, uint256 amount) public returns (bool);
```
This would indeed return a ‘false’ Boolean value if the transfer fails. Inside the initial function parameters, it would look like this:
```
function query(uint _amount, address _receiver, function(address, uint256) external returns (bool) transfer) public {
```
In order to make sure our own ‘query’ function would revert, we can use the require statement.
```
require(transfer(_receiver, _amount), "ERC20 transfer failed");
```
The overall function would look like this in regular solidity.
```
function query(uint _amount, address _receiver, function(address, uint256) external returns (bool) transfer) public {
    require(transfer(_receiver, _amount), "transfer failed");    
}
```


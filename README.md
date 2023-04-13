# solidity-gas-
在智能合约中使用solidity语言节约gas的一些方法：
一：在能替换memory的地方使用calldata进行替换可以节省gas😀；
二：当我们在判断的时候例如||把可能会true的结果写在前面，因为true了之后就不会再判断后面的了，可以节约gas😀；
三：当我们在判断的时候例如&&把可能会false的结果写在前面，因为false了之后就不再判断后面的，可以节约gas😀；
四：多使用view，因为view是只读的，不会消耗gas；
五：执行完所有的逻辑之后在更新storage的变量；
⑤例如contract jiangjiang {
uint public a = 0;
function A() public {
for(uint i = 0; i < 5; i++) {
a++;}
}
}
而我们修改之后呢👇

contract jiangjiang {
uint public a = 0;
function A() public {
uint aclone;
for(uint i = 0; i < 5; i++) {
aclone++;}
a = aclone;}
}
六：定义数组的时候固定长度可以节省gas😀；
例如uint[2] public arr;就比uint[] public arr更省gas
用require代替assert，并且让error statement尽量的简洁
例如require(a > 10, "not more than 10");
暂时就这些吧🤔，以后还有什么方法我还会再更新
谢谢大家阅读我的这些大白话😂😂😂

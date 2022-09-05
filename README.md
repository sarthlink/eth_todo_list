# TodoList Dapp




## Goal

While a TodoList app is not suited to ethereum-based backends, I originally wanted to do one to get my hands on this technology and to have a very simple app actually doing something I am familiar with as a front-end developer.



## Required dependencies

### A running node

You must run a node on your computer, whether its a real or virtual one. For development speed reasons, the best choice is to use testrpc because you have as much ether as you want and don't need to mine transactions.

#### Install instructions

##### Mac & Linux

```js
sudo npm install -g ethereumjs-testrpc
```

##### Windows

[The ethereumjs-testrpc package needs much more things to be installed on your machine to work on Windows.](https://github.com/ethereumjs/testrpc/wiki/Installing-TestRPC-on-Windows)






### Truffle - Compile & Migrate contracts to the blockchain

```
sudo npm install -g truffle
```



```
npm install
```



### Run your ethereum node

#### With testrpc

In a terminal (or in vagrant ssh on Windows, see above), run ```testrpc```

#### With Geth

##### Locally



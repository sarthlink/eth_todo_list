# TodoList Dapp

## Live demo

![ethereum-todolist-demo](https://cloud.githubusercontent.com/assets/8942633/24293643/108c3a9c-1093-11e7-9cee-8f162145eb89.gif)

## Goal

While a TodoList app is not suited to ethereum-based backends, I originally wanted to do one to get my hands on this technology and to have a very simple app actually doing something I am familiar with as a front-end developper.

The goal of this sample app is to help anyone wanting to understand what are ethereum contracts and how they can be used as a distributed back-ends, with its limitations as well.

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

If you can't afford this, we've covered you with [*Vagrant*](https://www.vagrantup.com/). This piece of software allows you to run a lightweight linux virtual machine in the terminal. Thus, it uses much less power than a full VM and you can still enjoy your Windows environment and tools you are used to, while providing you linux compatibility for terminal tools.

To do so, it's as easy as:

- [**Downloading and installing Vagrant**](https://releases.hashicorp.com/vagrant/1.9.2/vagrant_1.9.2.msi?_ga=1.13795955.512399365.1487957654)
- Run ```vagrant up``` in a terminal opened at the project root. It may take some time as it must download an ubuntu ISO the first time it runs.
- Then run ```vagrant ssh```. If it doesn't work (it probably won't in fact) you can use **Git bash** if you already have it on your computer. If you don't, [follow those instructions](http://tech.osteel.me/posts/2015/01/25/how-to-use-vagrant-on-windows.html).

And that's it ! Now you can run ```testrpc``` and you should see your node running.

### Truffle - Compile & Migrate contracts to the blockchain

```
sudo npm install -g truffle
```

> **Note :** ```npm install -g truffle``` on Windows.

## Instructions

### Setting up the devTools and client dependencies

```
npm install
```

> **Note :** If install fails on windows (particularly if node-gyp is the issue), run Powershell as administrator and run ```npm install -g windows-build-tools```. It will allow you to install and use native node packages.

### Run your ethereum node

#### With testrpc

In a terminal (or in vagrant ssh on Windows, see above), run ```testrpc```

#### With Geth

##### Locally

- [Install Ethereum on your machine](https://github.com/ethereum/go-ethereum/wiki/Building-Ethereum)
- ```npm run geth``` to initialize and run the ethereum node with geth console
- ```personal.unlockAccount("ACCOUNT_TO_UNLOCK_ADDRESS", "pass")``` (see Note if you don't get it)
- ```miner.start()```

**Note :** At least the first time, you need to run those commands to create an account to mine on

- ```personal.newAccount("pass")```
- ```personal.unlockAccount("ACCOUNT_ADDRESS", "pass")```

**Note 2:** If you need to customize the geth parameters, check the "geth" task in gulpfile.js.

### Deploy the smart contracts to the node

In another terminal, run ```truffle compile``` and then ```truffle migrate --reset```

**Warning here:** You have to re-run those commands when you modify your contracts so that they are re-deployed to the blockchain.

> **Note :** There is an experimental watcher that launch these commands when you save a contract.
> It may not work but it's worth the shot : ```npm run watch-contracts```

### Running the client app

With your node running and the smart contracts deployed to it, run in terminal ```npm start```.

You're done !

## FAQ

* __Why is there both a truffle.js file and a truffle-config.js file?__

    Truffle requires the truffle.js file be named truffle-config on Windows machines. Feel free to delete the file that doesn't correspond to your platform.

* __Where is my production build?__

    The production build will be in the build_webpack folder. This is because Truffle outputs contract compilations to the build folder.

* __Where can I find more documentation?__

    This project has been created with [truffle-box-react](https://github.com/truffle-box/truffle-box-react/) which is a marriage of [Truffle](http://truffleframework.com/) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start!
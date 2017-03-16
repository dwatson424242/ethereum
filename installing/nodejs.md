# NodeJS Install

## Installation

Install Git

```sh
$ sudo yum install git
```

Install Homebrew for Linux

```sh
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Linuxbrew/install/master/install)"
```

Add Homebrew executables to PATH

```sh
$ echo 'export PATH="$HOME/.linuxbrew/bin:$PATH"' >>~/.bash_profile
$ echo 'export PATH="/home/ec2-user/.linuxbrew/sbin:$PATH"' >> ~/.bash_profile
$ source ~/.bash_profile
```

Install C Development Tools and Screen

```sh
$ sudo yum groupinstall 'Development Tools'
$ sudo yum groupinstall screen
```

Install Node.js 

```sh
$ brew update && brew install -v node 
```

Install Ethereum testrpc

```sh
$ npm install -g ethereumjs-testrpc
```

## Running & Testing

### TestRPC 

To run testrpc, the easiest way is to use screen. SSH to the server in a new tab.

```sh
$ screen
$ testrpc
```
At this point you will be able to close the testrpc tab and it will keep running in the background.  To connect in another session to the screen instance, use  **screen -ls** to list all the sessions and **screen -r instance-name** to reconnnect.

### Setting up NodeJS

To build your nodejs app, run the following commands:

```sh
$ mkdir ethereum
$ cd ethereum/
$ vim package.json
```

Create pacakge.json file

```JSON
{
  "dependencies": {
    "web3": "0.17.0-alpha"
  }
}
```

Now install the dependencies from the ethereum directory

```sh
$ npm install
```

Now you can run the node console

```sh 
$ node
```

Now type the following commands 

```JavaScript
var Web3 = require("web3")

var web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"))

web3.eth.accounts
```

If web3.eth.accounts matches the account in your testrpc, you are good to go

	
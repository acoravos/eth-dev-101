# eth-dev-101
Playing around with Alex Miller's [Getting Started as an Ethereum Web Developer](https://hackernoon.com/getting-started-as-an-ethereum-web-developer-9a2a4ab47baf). 

Cryptography Intependent Project @ Harvard University, Spring 2017. 

## Guide to manually execute transactions using testrpc and truffle

### Step 1: Get a blockchain set up on our computers
There are lots of clients to choose from (e.g., geth, parity, and many others). We went with [testprc](https://github.com/ethereumjs/testrpc), because it's perhaps the fastest Ethereum RPC client for testing and development. We also didn't have to download any parts of the existing blockchain.

### Step 2: Set up the other frameworks and infrastructure 
We used [Truffle](https://github.com/trufflesuite/truffle), one of the most popular Ethereum development frameworks. We also used Web3, an Ethereum JavaScript API.

If you haven't already, install [testprc](https://github.com/ethereumjs/testrpc), [Truffle](https://github.com/trufflesuite/truffle) and [Web3](https://github.com/ethereum/web3.js).

### Step 3: Execute & Play.

We wanted to do some simple transactions to get familar with the Ethereum protocol. Here's a short guide on how we did it. 

Activate the testprc
```
$testrpc
```

This gave us nine available accounts and private keys to play with.

![testrpc_accounts](/img/testrpc_accounts.png)

Next, deploy the contracts using the Truffle console, which has access to the Web3 API. Open a new terminal and type `$truffle deploy` and then `$truffle console`. 

Inside the console, tested out a few [activities using Web3](https://github.com/ethereum/wiki/wiki/JavaScript-API). 

#### Sending Ether
_For reference in our screenshots, we set `eth = config.web3.eth`._

To send a transacton from one account to another
```
eth.sendTransaction({from: eth.accounts[0], to: eth.accounts[1], value: web3.toWei(1, "ether")});
```
![send_transaction](/img/send_transaction.png)

We sent 1 wei from account[0] to account[1].

#### Check Balance
We could then check the balance of the two accounts to see if our transaction was successful. 

![get_balance](/img/get_balance.png)

Yay.

#### Checking receipts.
Given that we have the transactionHash, we can find out how much gas was used and other details about the transaction by typing `eth.getTransactionReceipt(transactionHash)`.

![check_receipt](/img/check_receipt.png)

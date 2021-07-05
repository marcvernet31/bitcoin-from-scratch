# toy-bitcoin


This project is an attempt to code a DIY clone of Bitcoin with similar functionalities. The goal was to learn firsthand the inner working of cryptocurrency more than having a functional final product (which is absolutely not haha).

### Functionalities
There's a fully working blockchain where blocks storing data can be appended via a Proof of Work algorithm based in sha256. The blockchain can be stored in a pickledb database and be retrieved later to continue the chain from the last block. 
The blockchain can be initiated automatically with a Genesis block.

Transactions can be created, serialized and stored into the blockchain, and retrieved from blocks stored in the database. For every new block minted a coinbase transaction is generated, with a constant reward for the miner.

It's also possible to generate wallets, with private and public keys based on the ecdsa algorithm and an adress based on the bitcoin hashing methods.

## How to use it

To start the program run the `cli.py` script:
```
>$ python3 cli.py
```
On start the scripts asks the user to generate a new wallet that will mint the genesis block and initiate the blockchain
```
Creating user wallet to Init BlockChain ...
User alias: marc
Your adress is: EX4dHCYX2E6oMjDVVUTJkYnd7gfr2phno
Private Key stored in marc_pk.txt
--------------------------------------------------
Retrieving last block or generating genesis block
First Block PrevHash: 0006ccd03b004b4ca20c96640c50156d1c985c9460fc166db94266a3ccc6bc7b
First Block Hash: 000a97dfc57a4ff70be65864f9aaca22d135ed3b423b0e58a3ac653985a7b65a
--------------------------------------------------
```
### Wallets
To generate a new wallet is just necessary to input an alias, this is just a name for the wallet that will make it easier that using the address during the transaction. (doesn't exist in bitcoin but it makes a lot easier to use the blockchain from the terminal). 
After generating the wallet, the private key will be stored in a text file.
```
Input new order: wallet
User alias: marc
Your adress is: EUfxaAboQ2zjp5LmJ8dhHDqnfEaJbaXK7
Private Key stored in marc_pk.txt
```
### Transactions
To input a new transaction to the ledger it's necessary to input our alias, the destiny address and the link to the file with our private key. After verifying the private key a prompt to input the value to transact will appear.
```
Input new order: transaction
User alias: marc
Destiny adress: 0006ccd03b004b4ca20c96640c50156d1c985c9460
Key file path: marc_pk.txt
----- Correct key -----
Value to transfer: 100
----- Transaction introduced to ledger, add block to execute -----
```
### Add block
Only after creating a new block and adding it to the blockchain the previous transactions will be stored and "executed". When a block is added to the blockchain the mining is done by the user or wallet that performs the action, and so a coinbase transaction is created and added to the block to reward the creator.
```
 Input new order: add
User alias: marc
Key file path: marc_pk.txt
----- Correct key -----
---- Executing transaction ---- 93f0734a00ac1590f3b9fc39fc1c6296e51ab8f508e2869b558dd800e959447f
From adress: EUfxaAboQ2zjp5LmJ8dhHDqnfEaJbaXK7
To adress: 0006ccd03b004b4ca20c96640c50156d1c985c9460
Value: 100
--------------------------------------------------
---- Executing transaction ---- b772ae14259d27265de17a4b600b600158d4ae02a61dbe6ee462f086719ac101
Coinbase transaction
To adress: EUfxaAboQ2zjp5LmJ8dhHDqnfEaJbaXK7
Value: 100
--------------------------------------------------
```

## Why Python 
Original Bitcoin is mostly developed in C++, and most of similiar projects of creating mock criptocurrencies that I could find used other languages than Python. Python seemed very underprepresented, so I choosed Python purely for the challenge, knowing that it's not a good choice for this project (working at byte level with Python is hell).
As a positive discovery, both pickledb and hashlib used in the project are very cool libraries. 

## To do
#### Persistence of wallets
Persistence of the blockchain is solved with pickledb, but when the script is closed all the wallet information is erased. The wallets could be stored more or less easily with the same aproach, but I was tired to fight with json formats.

### Wallet - Transaction link
The blockchain allows to input transactions from wallets and store them, but it's not possible to calculate balances. The transaction input from wallets is a temporal solution to have working transactions, but it doesn't work the same way bitcoin transactions work, so it needs to be solved in a future.

### Distributed Proof-Of-Work
It would be cool to be able to run several PoW users to allow competition in block mining.

## Developer

[![marcvernet31](https://avatars.githubusercontent.com/u/44305244?s=400&u=aeac841bfd0fe52cf15d975b5d9825dbab4c73b8&v=4)](https://github.com/marcvernet31) | 
| --- | 
| [Marc Vernet](https://github.com/marcvernet31) |

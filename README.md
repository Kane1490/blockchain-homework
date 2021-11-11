# blockchain-homework
Homework week 18 Blockchain

Create a new project directory for your new network. This was called zbank2

Create accounts for two (or more) nodes for the network with a separate datadir for each using geth. We called the nodes: node21 and node22

This was done by using: 

./geth account new --datadir node21
and
./geth account new --datadir node22

Make sure to save the adress and path of secret file key as we will use these later. 
Ensure to remember Chain ID, ours was 123, and any passwords set (we did not set any passwords)


Run puppeth, name your network, and select the option to configure a new genesis block. (1)
./puppeth

Choose the Clique (Proof of Authority) consensus algorithm. (2)


Paste both account addresses from the first step one at a time into the list of accounts to seal.
The 0x is pre filled, so remeber to not add twice!
0xEEa4952D6c75a77da752dFdD5308d76E338cbf30
0x038d59D11e0268b8862eCA30551ed61a84F053AA

Paste them again in the list of accounts to pre-fund. There are no block rewards in PoA, so you'll need to pre-fund.


You can choose no for pre-funding the pre-compiled accounts (0x1 .. 0xff) with wei. This keeps the genesis cleaner.


Complete the rest of the prompts, and when you are back at the main menu, choose the "Manage existing genesis" (2) option.


Export genesis configurations. This will fail to create two of the files, but you only need zbank2.json.


You can delete the zbank2-harmony.json file.


Screenshots can be found in screenshot folder.


Initialize each node with the new networkname.json with geth.
./geth init zbank2.json --datadir node21
and 
./geth init zbank2.json --datadir node22

Run the first node, unlock the account, enable mining, and the RPC flag. Only one node needs RPC enabled.
./geth --datadir node21 --unlock "eea4952d6c75a77da752dfdd5308d76e338cbf30" --mine --rpc --allow-insecure-unlock --minerthreads 1

We didnt set a password, so just push enter when prompted for password.
Make sure to copy the text after self= enode... as this is needed for the second node

Set a different peer port for the second node and use the first node's enode address as the bootnode flag.
./geth --datadir node22 --unlock "038d59d11e0268b8862eca30551ed61a84f053aa" --mine --port 30304 --bootnodes "enode://b98199cdaaa8ea63535dde485330be0a7616e8d67a037d5e404c8849f520e59dbc2b6877b431a79932caaf9c5943e9ffa7e5f42fc0df9b208440210620c8bc1d@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

We didnt set a password, so just push enter when prompted for password.

The nodes should now be producing new blocks!

Use the MyCrypto GUI wallet to connect to the node with the exposed RPC port.

You will need to use a custom network, and include the chain ID, and use ETH as the currency. 
This is done by selecting change network, then add custom node. Node name is zbank2, and we retrieve our chain ID that we saved before (123)

Import the keystore file from the node21/keystore directory into MyCrypto. This will import the private key.


Send a transaction from the node21 account to the node21 account.


Copy the transaction hash and paste it into the "TX Status" section of the app, or click "TX Status" in the popup.


See screenshot of transaction in screenshots folder!



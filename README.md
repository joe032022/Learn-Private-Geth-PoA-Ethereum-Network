# Learn Private Geth PoA Ethereum Network
`Note: "Should use virtual machine form AWS or Azure or any other Cloud Service provider."`
- Can also run it on local machines for testing pourposes.

## why build pvt blockchain?
- privacy 
- can set own time and block.

`Note: "At least create 3 nodes or create odd number of nodes."`

## Prerequisite:
- `install geth`
-  metamask

## Create node 1 and node 2:
`node1/`
`>> geth --datadir "./data" account new`

`node2/`
`>> geth --datadir "./data" account new`

## Genesis Block Setup:
`>> puppeth`

`Clique : proof-of-authority` : Because we are building Pvt blockchain network.

- admin has to authorise one node for trasactions. 
- all the blocks will be mined from node1. 
- but node2 part of network but won't mine any blocks. 
chain id : give random number

- export genesis config(blockpoc.json): of `blockpoc` network  

run this command within 2 nodes.
- `geth --datadir ./data init ../blockpoc.json` 
- Now the 2 node run with the same genesis.

## Create Boot Node:
- Boot node is a node which is part of the network but it won't mine any blocks.
- It connects to all the nodes.
- `bnode/`:  
    -  `bootnode -genkey boot.key` 
    -  `bootnode -nodekey boot.key`
- the enode is passed to node1 and node2.This will allow other peers to connect to the network.
## Connect all the Nodes:
- `bootnode -nodekey "./boot.key" -verbosity 7 -addr "127.0.0.1:30301"`
- `node1/`: `geth --networkid 14333 --datadir "./data" --bootnodes [bootnode enode] --port 30303 --ipcdisable --syncmode full --http --allow-insecure-unlock --http.corsdomain "*" --http.port 8545 --unlock [public address node1] --password password.txt --mine console`
- `node2/`: `geth --networkid 14333 --datadir "./data" --bootnodes [bootnode enode] --port 30304 --ipcdisable --syncmode full -http --allow-insecure-unlock --http.corsdomain "*" --http.port 8546 --unlock [public address node2] --password password.txt console`

## Deploy Smart Contract:
- run bootnode, then node1(network will be up and running), then run node2(which doesn't).
-  create network in metamask 
-  then run a smart contact in newly created pvt network.

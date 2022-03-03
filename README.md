# Learn Private Geth PoA Ethereum Network
- Should use virtual machine form AWS or Azure or any other Cloud Service provider.

## why build pvt blockchain?
- privacy 
- can set own time and block.

`At least create 3 nodes or create odd number of nodes.`

- `install geth`
## Create node 1 and node 2:
`node1/`
`>> geth --datadir "./data" account new`

`node2/`
`>> geth --datadir "./data" account new`

## Genesis Block Setup:
`>> puppeth`

Clique - proof-of-authority
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

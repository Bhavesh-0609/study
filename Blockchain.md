# Blockchain
# Blockchain intuition
## What is a blockchain
>stuart haber and w. scott stornetta in 1991 published a paper called how to time stamp a digital document and if you look through the paper you read through it you'll find the concept of what now we call a blockchain and all or most of the feature and ideas behind the blockchain actuall are present in that paper.
>
>defination by wikipedia : A blockchain is a continuously growing list of records, called blocks, which are linked and secured using cryptography.
>
>Genesis block : in blockchain the fist block is called as genesis block

## Understanding SHA256 - Hash
> Hashes are like fingerprints
>
> The algorithm behind SHA256 was developed by NSA (National Security Agency)
>
> In SHA256, SHA stand for **Secure Hash Algorithm** and **256 is number of bits it takes up in memory**
>
> SHA256 hash is 64 characters long and 1 character take 4 bits 
>
> Data to SHA256 converter : https://tools.superdatascience.com/blockchain/hash

> ### The 5 requirements for hash algorithms
>   1. One-way : you cannot go from the hash to the document/content so you cannnot restore or reverse engineer the document based on the hash.
>   2. Deterministic : if the documents/data are the exactly same then the hashes are exactly same.
>   3. Fast computation
>   4. The avalanche effect : if the 2 documents/data are exactly same then we get exactly same hash but if we change one of them minor than the hash will change completly diffrent.
>   5. Must withstand collisions

>![image](https://user-images.githubusercontent.com/92302123/151661334-089aa1a6-4eca-4e62-b45b-7a7d379ebafe.png)
## Immutable ledger
>The word Immutable means “cannot be changed.” And ledger is a fancy term for record, a record of something. Therefore an Immutable Ledger is a record that cannot be changed. In the digital age we need data security and proof that the data has not been altered -- that's the only way we can trust the digital data.
## Distributed P2P network
>Peer-to-peer (P2P) computing or networking is a distributed application architecture that partitions tasks or workloads between peers. Peers are equally privileged, equipotent participants in the application. They are said to form a peer-to-peer network of nodes.
>
>![image](https://user-images.githubusercontent.com/92302123/151701890-8a28c982-5bf3-4429-847f-41e990b641ed.png)
## nonce 
>What is nonce used for?
>A nonce in cryptography is a number used to protect private communications by preventing replay attacks. Nonces are random or pseudo-random numbers that authentication protocols attach to communications.
## Byzantine fault tolerance
> ![image](https://user-images.githubusercontent.com/92302123/151703887-584c2444-0d1a-4a74-b295-984d8103e640.png)
>
> https://people.eecs.berkeley.edu/~satishr/cs273.01/p382-lamport.pdf
>
>![image](https://user-images.githubusercontent.com/92302123/151703948-79917e7a-79ca-4617-9054-22e7c7d50840.png)
>
>https://medium.com/loom-network/understanding-blockchain-fundamentals-part-1-byzantine-fault-tolerance-245f46fe8419
# Create a blockchain
## Step 1
>   - Install anaconda and launch spyder
## Step 2
>   - Open anaconda prompt and install flask. command = "pip install Flask==0.12.2"
>   - Download postman
## Step 3
>   - Importing the libraries
>     - import datetime
>     - import hashlib
>     - import json
>     - from flask import Flask, jsonify
## Step 4
```
# Module 1 - Create a blockchain

# To be installed:
    # Flask==0.12.2: pip install Flask==0.12.2
    # Postman HTTP client: https://www.getpostman.com

# importing the libraries
import datetime
import hashlib
import json
from flask import Flask, jsonify

# Part 1 - Building a blockchain

class Blockchain:
    
    def __init__(self):
        self.chain = [] # created an empty chain
        self.create_block(proof = 1, previous_hash = '0') # creating genesis block(first block)
```

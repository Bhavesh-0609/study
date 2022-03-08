# Blockchain
# Blockchain intuition
## What is a blockchain
>stuart haber and w. scott stornetta in 1991 published a paper called how to time stamp a digital document and if you look through the paper you read through it you'll find the concept of what now we call a blockchain and all or most of the feature and ideas behind the blockchain actuall are present in that paper.
>
>defination by wikipedia : A blockchain is a continuously growing list of records, called blocks, which are linked and secured using cryptography.
>
>Genesis block : in blockchain the first block is called as genesis block

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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
```
## Step 5
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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
    
    def get_previous_block(self):
        return self.chain[-1] # returning previous block
```
## Step 6
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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
    
    def get_previous_block(self):
        return self.chain[-1]
    
    def proof_of_work(self, previous_proof):
        new_proof = 1 # creating new proof variable and assigning default value = 1
        
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexdigest() # solving problem and creating hash
            if hash_operation[0:4] == '0000': # validing generated hash
                check_proof = True
            else:
                new_proof += 1
        return new_proof
```
## step 7
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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
    
    def get_previous_block(self):
        return self.chain[-1]
    
    def proof_of_work(self, previous_proof):
        new_proof = 1 # creating new proof variable and assigning default value = 1
        
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexdigest() # solving problem and creating hash
            if hash_operation[0:4] == '0000': # validing generated hash
                check_proof = True
            else:
                new_proof += 1
        return new_proof
    
    def hash(self, block):
        encoded_block = json.dumps(block, sort_keys = True).encode() # coverting block in string
        return hashlib.sha256(encoded_block).hexdigest() # converting block string in hash
```
## Step 8
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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
    
    def get_previous_block(self):
        return self.chain[-1]
    
    def proof_of_work(self, previous_proof):
        new_proof = 1 # creating new proof variable and assigning default value = 1
        
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexdigest() # solving problem and creating hash
            if hash_operation[0:4] == '0000': # validing generated hash
                check_proof = True
            else:
                new_proof += 1
        return new_proof
    
    def hash(self, block):
        encoded_block = json.dumps(block, sort_keys = True).encode() # coverting block in string
        return hashlib.sha256(encoded_block).hexdigest() # converting block string in hash
    
    def is_chain_valid(self, chain):
        # authanticating blockchain
        previous_block = chain[0]
        block_index = 1
        while block_index < len(chain):
            # validating hash
            block = chain[block_index]
            if block['previous_hash'] != self.hash(previous_block):
                return False
            # validating proof
            previous_proof = previous_block['proof']
            proof = block['proof']
            hash_operation = hashlib.sha256(str(proof**2 - previous_proof**2).encode()).hexdigest()
            if hash_operation[0:4] != '0000':
                return False
            # incrementing index and previous block
            previous_block = block
            block_index += 1
        return True
```
## Step 9
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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
    
    def get_previous_block(self):
        return self.chain[-1]
    
    def proof_of_work(self, previous_proof):
        new_proof = 1 # creating new proof variable and assigning default value = 1
        
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexdigest() # solving problem and creating hash
            if hash_operation[0:4] == '0000': # validing generated hash
                check_proof = True
            else:
                new_proof += 1
        return new_proof
    
    def hash(self, block):
        encoded_block = json.dumps(block, sort_keys = True).encode() # coverting block in string
        return hashlib.sha256(encoded_block).hexdigest() # converting block string in hash
    
    def is_chain_valid(self, chain):
        # authanticating blockchain
        previous_block = chain[0]
        block_index = 1
        while block_index < len(chain):
            # validating hash
            block = chain[block_index]
            if block['previous_hash'] != self.hash(previous_block):
                return False
            # validating proof
            previous_proof = previous_block['proof']
            proof = block['proof']
            hash_operation = hashlib.sha256(str(proof**2 - previous_proof**2).encode()).hexdigest()
            if hash_operation[0:4] != '0000':
                return False
            # incrementing index and previous block
            previous_block = block
            block_index += 1
        return True

# Part 2 - Mining our blockchain

# Creating a web app
app = Flask(__name__)

# Creating a blockchain
blockchain = Blockchain()
```
## Step 10
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
        
        
    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash} # creating block with dictionary
        self.chain.append(block) # adding created block in  list
        return block # returning created block for postman
    
    def get_previous_block(self):
        return self.chain[-1]
    
    def proof_of_work(self, previous_proof):
        new_proof = 1 # creating new proof variable and assigning default value = 1
        
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexdigest() # solving problem and creating hash
            if hash_operation[0:4] == '0000': # validing generated hash
                check_proof = True
            else:
                new_proof += 1
        return new_proof
    
    def hash(self, block):
        encoded_block = json.dumps(block, sort_keys = True).encode() # coverting block in string
        return hashlib.sha256(encoded_block).hexdigest() # converting block string in hash
    
    def is_chain_valid(self, chain):
        # authanticating blockchain
        previous_block = chain[0]
        block_index = 1
        while block_index < len(chain):
            # validating hash
            block = chain[block_index]
            if block['previous_hash'] != self.hash(previous_block):
                return False
            # validating proof
            previous_proof = previous_block['proof']
            proof = block['proof']
            hash_operation = hashlib.sha256(str(proof**2 - previous_proof**2).encode()).hexdigest()
            if hash_operation[0:4] != '0000':
                return False
            # incrementing index and previous block
            previous_block = block
            block_index += 1
        return True

# Part 2 - Mining our blockchain

# Creating a web app
app = Flask(__name__)

# Creating a blockchain
blockchain = Blockchain()

# Mining a new block
@app.route('/mine_block', method=['Get']) # mine block request, also called as route decorator
def mine_block():
    previous_block = blockchain.get_previous_block() # getting previous block
    previous_proof = previous_block['proof'] # getting previous proof
    proof = blockchain.proof_of_work(previous_proof) # getting proof
    previous_hash = blockchain.hash(previous_block) # getting previous hash
    block = blockchain.create_block(proof, previous_hash) # getting block
    response = {'message': 'Congratulations, you just mined a block!',
                'index': block['index'],
                'timestamp': block['timestamp'],
                'proof': block['proof'],
                'previous_hash': block['previous_hash']} # creating response dictionary
    return jsonify(response), 200
```
## Step 11
```
# Module 1 - Create a Blockchain

# To be installed:
# Flask==0.12.2: pip install Flask==0.12.2
# Postman HTTP Client: https://www.getpostman.com/

# Importing the libraries
import datetime
import hashlib
import json
from flask import Flask, jsonify

# Part 1 - Building a Blockchain

class Blockchain:

    def __init__(self):
        self.chain = []
        self.create_block(proof = 1, previous_hash = '0')

    def create_block(self, proof, previous_hash):
        block = {'index': len(self.chain) + 1,
                 'timestamp': str(datetime.datetime.now()),
                 'proof': proof,
                 'previous_hash': previous_hash}
        self.chain.append(block)
        return block

    def get_previous_block(self):
        return self.chain[-1]

    def proof_of_work(self, previous_proof):
        new_proof = 1
        check_proof = False
        while check_proof is False:
            hash_operation = hashlib.sha256(str(new_proof**2 - previous_proof**2).encode()).hexdigest()
            if hash_operation[:4] == '0000':
                check_proof = True
            else:
                new_proof += 1
        return new_proof
    
    def hash(self, block):
        encoded_block = json.dumps(block, sort_keys = True).encode()
        return hashlib.sha256(encoded_block).hexdigest()
    
    def is_chain_valid(self, chain):
        previous_block = chain[0]
        block_index = 1
        while block_index < len(chain):
            block = chain[block_index]
            if block['previous_hash'] != self.hash(previous_block):
                return False
            previous_proof = previous_block['proof']
            proof = block['proof']
            hash_operation = hashlib.sha256(str(proof**2 - previous_proof**2).encode()).hexdigest()
            if hash_operation[:4] != '0000':
                return False
            previous_block = block
            block_index += 1
        return True

# Part 2 - Mining our Blockchain

# Creating a Web App
app = Flask(__name__)
app.config['JSONIFY_PRETTYPRINT_REGULAR'] = False

# Creating a Blockchain
blockchain = Blockchain()
@app.route('/')
def home():
    return "hello world"
# Mining a new block
@app.route('/mine_block', methods = ['GET'])
def mine_block():
    previous_block = blockchain.get_previous_block()
    previous_proof = previous_block['proof']
    proof = blockchain.proof_of_work(previous_proof)
    previous_hash = blockchain.hash(previous_block)
    block = blockchain.create_block(proof, previous_hash)
    response = {'message': 'Congratulations, you just mined a block!',
                'index': block['index'],
                'timestamp': block['timestamp'],
                'proof': block['proof'],
                'previous_hash': block['previous_hash']}
    return jsonify(response), 200

# Getting the full Blockchain
@app.route('/get_chain')
def get_chain():
    try:
        response = {'chain': blockchain.chain,
                'length': len(blockchain.chain)}
        return jsonify(response)
    except:
        return jsonify({"error":"Error occured"})

# Checking if the Blockchain is valid
@app.route('/is_valid', methods = ['GET'])
def is_valid():
    is_valid = blockchain.is_chain_valid(blockchain.chain)
    if is_valid:
        response = {'message': 'All good. The Blockchain is valid.'}
    else:
        response = {'message': 'Houston, we have a problem. The Blockchain is not valid.'}
    return jsonify(response), 200

# Running the app
app.run(host = '0.0.0.0', port = 5000)
```
# Cryptocurrency Intuition 
## What we will learn in this section:
>   1. What is Bitcoin?
>   2. Bitcoin's monetary policy
>   3. Understanding mining difficulty
>   4. Virtual tour of a bitcoin mine
>   5. Mining pools
>   6. Nonce range
>   7. How miners pick transactions (Part 1)
>   8. How miners pick transactions (Part 2)
>   9. CPUs vs GPUs vs ASICs
>   10. How do mempools work?
>   11. Orphaned blocks
>   12. The 51% attack
>   13. Extra: Bits to target conversion
## What is Bitcoin?
>![image](https://user-images.githubusercontent.com/92302123/153756190-3b13d9cf-bcfd-4c4c-9ff7-3f5f9c4b5c88.png)
>
> Bitcoin is invented in 2008 by a person who were operating under the name `Satoshi nakamoto`
> 
> ![image](https://user-images.githubusercontent.com/92302123/153756971-24362162-c5c5-4d04-a2ba-f943abb9c525.png)
## Bitcoin's monetary policy
>![image](https://user-images.githubusercontent.com/92302123/153757113-621a0b9a-3307-4ec0-b1cc-30bbef4a7ba1.png)
>
>![image](https://user-images.githubusercontent.com/92302123/153757399-17db3cb1-0efc-48a4-84f9-3a1b8f682b28.png)
>
>![image](https://user-images.githubusercontent.com/92302123/153757506-ee0837ce-dc3e-48cc-9e42-c284825fd8f4.png)
>
## Understanding mining difficulty
> Here difficulty is find a hash who have 18 leading zeros.
> 
> And the answer is below.
> 
> ![image](https://user-images.githubusercontent.com/92302123/153763015-27f5af70-befa-44bd-9741-de5a36620f62.png)

> ### First mining difficulty of bitcoin
>![image](https://user-images.githubusercontent.com/92302123/153764348-70bd17c8-999b-40af-ad98-c2450efcca93.png)
## Mining pools
>A mining pool is a joint group of cryptocurrency miners who combine their computational resources over a network to strengthen the probability of finding a block or otherwise successfully mining for cryptocurrency.
>
> https://www.buybitcoinworldwide.com/mining/pools/
> 
> https://www.blockchain.com/charts/pools
## Nonce range
>![image](https://user-images.githubusercontent.com/92302123/155001670-f1a96a24-60c8-4bd9-8b6e-287caa19b83b.png)
>![image](https://user-images.githubusercontent.com/92302123/155001743-5fae9748-15b0-489c-a8a7-5f0f79b50988.png)
>
>in every block there is unix timestamp which change every second and thats why nonce validity change every second.
## How miner pick trasactions (part 1)
### what is mempool
> The mempool (memory pool) is a smaller database of unconfirmed or pending transactions which every node keeps. When a transaction is confirmed by being included in a block, it is removed from the mempool.

>In nonce range if any miner check all 4billion nonces less than in second than he can change block configuration like he will replace lowest transaction with other transaction and now he can go for other 4 billion nonces
## CPU's vs GPU's vs ASIC's
>![image](https://user-images.githubusercontent.com/92302123/155174250-1b6339ec-6ffb-4027-b50f-e25db6d60aa6.png)
### Ethereum memory hardnes
>https://www.vijaypradeep.com/blog/2017-04-28-ethereums-memory-hardness-explained

## How mempools works
>https://www.blockchain.com/btc/unconfirmed-transactions
## Converting block bits into current target
>![image](https://user-images.githubusercontent.com/92302123/155377707-2201afa0-0aa0-43ac-94f5-ccfbd92df82f.png)
# Cryptocurrency Transactions Intuition
## UTXO 
>What Is UTXO? The term UTXO refers to the amount of digital currency someone has left remaining after executing a cryptocurrency transaction such as bitcoin. The letters stand for `unspent transaction output.` Each bitcoin transaction begins with coins used to balance the ledger.
## Transection fee
> In UTXO if any btc left its count as transection fees
## How wallet works
> Wallet is just count you left UTXO's and show you on screen.
## Signature, public key and private key
>![image](https://user-images.githubusercontent.com/92302123/155754616-4afcd8e8-766c-49f8-8c73-5f024d9ddd67.png)
>With private key and message/transaction u can generate signature wich is always unique
>
>For validate the message/transaction u can use validation function (requirement : transaction, signature and public key for using this function)
## Signature and key demo
>https://tools.superdatascience.com/blockchain/public-private-keys/signatures
## What Is Segregated Witness (SegWit)?
>Segregated Witness (SegWit) refers to a change in the transaction format of Bitcoin. Its stated purpose as a protocol upgrade was to protect against transaction malleability and decrease transaction times by increasing block capacity. Transaction malleability refers to the possibility that tiny pieces of transaction information could be changed, invalidating new cryptocurrency blocks.
>
>It was also intended to speed up the validation process by storing more transactions in a block.
## Public key vs Bitcoin address
> Public keys are generated with eliptil function using private key and public address are generated with SHA256 using public key
## Hierarchically Deterministic (HD) Wallets
>A hierarchical deterministic (HD) wallet is a digital wallet commonly used to store the digital keys for holders of cryptocurrencies such as Bitcoin and Ethereum. Anyone with a copy of both the public and password-like private key can control the cryptocurrency in the account.
# Smart contract intuition
## Plane of attack
### What we will learn in this section:
>   1. What is ethereum?
>   2. What is a smart contract?
>   3. Decentralized application (Dapps)
>   4. Ethereum virtual machine & gas
>   5. Decentralized autonomous organizations (DAOs)
>   6. The DAO attack
>   7. Soft and hard fork (Part 1)
>   8. Soft and hard fork (Part 2) (Advanced tutorial)
>   9. Initial coin offerings (ICOs)
>   10. ICO case study
>   11. Blockchain startups: White papers
>   12. Blockchain and Web 3.0
## What is a smart contract?
> solidity is programing language and its used for ethereum blockchain and there is also bitcoin script which used for bitcoin blockchain
> 
> bitcoin-script is not-turing complete but solidity is. (There is no loops in bitcoin-script)
> 
> In ethereum blockchain
>   - Each node has:
>       - History of all smart contracts
>       - History of all transactions
>       - current state of all smart contracts
## Decentralized applications (DApps)
> It contains an interface for people to interact with something a blockchain
> So DApp consists of a front end and a back end which is the smart contract
## Ethereum Virtual Machine
>The Ethereum Virtual Machine is the software platform that developers can use to create decentralized applications (DApps) on Ethereum. This virtual machine is where all Ethereum accounts and smart contracts live.
>### Gas
>Gas fees are payments made by users to compensate for the computing energy required to process and validate transactions on the Ethereum blockchain. "Gas limit" refers to the maximum amount of gas (or energy) that you're willing to spend on a particular transaction.
## What are DAOs?
>DAOs are an effective and safe way to work with like-minded folks around the globe.
>
>Think of them like an internet-native business that's collectively owned and managed by its members. They have built-in treasuries that no one has the authority to access without the approval of the group. Decisions are governed by proposals and voting to ensure everyone in the organization has a voice.
>
>There's no CEO who can authorize spending based on their own whims and no chance of a dodgy CFO manipulating the books. Everything is out in the open and the rules around spending are baked into the DAO via its code.
## Soft and hard fork
> Hard fork = loosen rules
> 
> Soft fork = tighten rules
> ![image](https://user-images.githubusercontent.com/92302123/156811130-a9b47415-cb25-400d-b557-429fac59d306.png)
## ICO (Initial coin offering)
> a process or event in which a company (especially a start-up) attempts to raise capital by selling a new cryptocurrency, which investors may purchase in the hope that the value of the cryptocurrency will increase, or to later exchange for services offered by that company.
> ![image](https://user-images.githubusercontent.com/92302123/156811172-144fac3d-50b6-4be4-a544-95d0cbd217c2.png)

# Solidity
```
// HadCoin ICO

// Version of compiler
pragma solidity ^0.4.11

contract hadcoin_ico{

    // Intreducing the maximum number of hadcoin available for sale
    uint public max_hadcoins = 1000000;

    // Introducing the USD to hadcoin conversion rate
    uint public usd_to_hadcoins = 1000;

    // Introducing the total numbers that have bought by investors
    uint public total_hadcoin_bought = 0;

    // Mapping from the investors address to its equity in hadcoin and usd
    mapping(address => uint) equity_hadcoin;
    mapping(address => uint) equity_usd;

    // Checking if an investor can by hadcoin
    modifier can_buy_hadcoin(uint usd_invested){
        require(usd_invested * usd_to_hadcoins + total_hadcoin_bought <= max_hadcoins);
        _; // its mean that the function will only execute when above condition is true
    }
}
```

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

> ### Fist mining difficulty of bitcoin
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

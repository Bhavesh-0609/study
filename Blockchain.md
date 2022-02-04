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
@app.route('/mine_block', methods=['Get'])
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

# Getting the full blockchain
@app.route('/get_chain', methods=['Get'])
def get_chain():
    # getting chain list from blockchain class and length of chain
    response = {'chain': blockchain.chain,
                'length': len(blockchain.chain)}
    return jsonify(response), 200

# Running the app
app.run(host = '0.0.0.0', port = 5000)
```

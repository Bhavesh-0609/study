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

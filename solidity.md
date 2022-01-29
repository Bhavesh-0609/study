# solidity
# What is ethereum
## What is ethereum
> Ethereum is a platform powered by blockchain technology that is best known for its native cryptocurrency, called ether, or ETH, or simply ethereum. The distributed nature of blockchain technology is what makes the Ethereum platform secure, and that security enables ETH to accrue value.
> 
> ![2022-01-25](https://user-images.githubusercontent.com/92302123/151005986-5b640907-036c-4f20-afa2-4df7224348dd.png)

>### What is node?
>- A blockchain consists of numerous blocks of data. These blocks of data are stored on nodes that can be compared to small servers. On a blockchain, all the nodes are connected to each other and they continuously exchange the newest information on the blockchain with each other.
>- Any one rune a node and any one can create node.
>- Each node that we create or i should say each node on the network has a full and separate copy of the blockchain.
## Interfacing with ethereum networks
> There's kind of two diffrent groups of technologies that we need to be aware of for connecting to the network.
> 
> ![2022-01-25 (1)](https://user-images.githubusercontent.com/92302123/151012217-2aa3417b-f051-412c-a883-1edc8f797e13.png)

> ### What is web3.js?
>- Web3.js is a collection of libraries which allow you to interact with a local or remote ethereum node, using a HTTP or IPC connection. The web3 JavaScript library interacts with the Ethereum blockchain. It can retrieve user accounts, send transactions, interact with smart contracts, and more.

> ### What is metamask?
>- MetaMask is a software cryptocurrency wallet used to interact with the Ethereum blockchain. It allows users to access their Ethereum wallet through a browser extension or mobile app, which can then be used to interact with decentralized applications.

> ### What is mist browser
>- The Mist browser was an Ethereum interface intended to allow users to access the various dApps available on the Ethereum network. It was also known as the Ethereum dApp Browser. ... As a DApp browser, Mist was a standalone application with a graphical user interface (GUI) that allowed users to sync to the blockchain.
## Ethereum account
> Firts create account on metamask (crome extension)
> When metamask created an account for us, it created an account that has three distinct pieces of information an account address, a public key and a private key. These are the three pieces of information that constitute an account on the ethereum network.
>- Account address : the account address can be thought of as essentially being like an email address.
>   - it's a unique identifier that can be shared with anyone in the world, and it tell other people who you are, identifies your account in some fashion.
>- Public and private key : These two pieces of information combined together to essentially form a password of sorts.
>   - The public key and the private key are used to authorize the sending of funds from your account  to other accounts.
>   - so if someone does not have the private key to an account, they don't have true access to any of the funds that are assigned to that account.
>
>#### *The account address, public and private key, are all stored as hexadecimal numbers*
>
>Example
>![2022-01-25 (5)](https://user-images.githubusercontent.com/92302123/151023831-efecd114-b201-4e58-9406-2548c05684ea.png)
## Receiving ethers
> For receive ether to your metamask account use this website https://rinkeby-faucet.com/ it will give you 0.001 ether at once
>
> What is happening behind the scene in this website
>![2022-01-25 (6)](https://user-images.githubusercontent.com/92302123/151026563-6a9aa15d-092a-4669-b758-3bd9bdeff95b.png)
>![2022-01-25 (7)](https://user-images.githubusercontent.com/92302123/151029179-982efe57-22d6-4467-aa2e-cd1307af06d7.png)
>![2022-01-25 (8)](https://user-images.githubusercontent.com/92302123/151031220-ee3df886-58c4-4d9c-8655-20d863193618.png)
![2022-01-25 (9)](https://user-images.githubusercontent.com/92302123/151031253-c26bb158-58fe-4849-a0f3-f443eeb4064f.png)
![2022-01-25 (10)](https://user-images.githubusercontent.com/92302123/151031254-5363c918-78e9-4a3c-8837-3de78fe0d062.png)
## Blockchain
> ### visual of blockchain : https://andersbrownworth.com/blockchain
## Smart Contracts
>![2022-01-26](https://user-images.githubusercontent.com/92302123/151209449-2c1c81e8-459d-4fdc-a88d-4b4a3a2cdbe6.png)
>
> Right now, you can imagine a smart contract as being an account, just like the one that you and created on metamask. but rather than being controlled by a human being like you and me, it is controlled by some amount of code. and this is code that you and i or a developer in general is going to author. this code instructs the smart contract how to behave.
>
> Let's talk about some of the diffrent properties that are contained within a smart contract account.
> ![2022-01-26 (1)](https://user-images.githubusercontent.com/92302123/151211081-064a6090-c6c8-4bd0-9604-5d4d5171f342.png)

> ### External account
> ![2022-01-26 (2)](https://user-images.githubusercontent.com/92302123/151212046-52833367-04fd-4e42-8439-876ff7250a9d.png)
>   - External accounts are any account that you and i or a human being or an entity owns.
>   - Remember that we had said that external accounts live in their own type of universe and they're completely decoupled from any individual network.

> ### Contract account
>   - These contract accounts are only specific to one individual network.
>   - So when we create a contract account that contains our smart contract, we create it on one specific network and they cannot be accessed across networks.
>   ![2022-01-26 (3)](https://user-images.githubusercontent.com/92302123/151213476-07f02509-327d-49d6-b1c6-ec7350e9a67e.png)

> So this is the actual code that instructs the contract, how it should behave and ho it should handle money.
> 
> we will then take that contract code, that source code and deploy it to a network like say, Rinkeby.
> 
> when we deploy this contract code, it creates an instance of the contract or what we refered to as the contract account.

## The solidity programming language
> Solidity is an object-oriented programming language, meaning that it is organized by data or objects rather than functions or logic. Its main purpose is for developing smart contracts for the Ethereum blockchain.
## First solidity code
```
pragma solidity ^0.4.17; // specifies the version of solidity that our code is written with

contract Inbox{ // define a new contract (remmember classes!) that will have some number of methods and variables
    string public message; // declares all of the instance variables (and their types) that will exist in this contract

    // defines different functions that will be members of this contract
    function Inbox(string initialMessage) public { // constructure
        message = initialMessage;
    }

    function setMessage(string newMessage) public {
        message = newMessage;
    }
    
    function getMessage() public view returns (string) {
        returns message;
    }
}
```
## Function Declararion
> ![2022-01-26 (4)](https://user-images.githubusercontent.com/92302123/151223208-4ab6695b-874e-499a-a114-155be0191a62.png)
## Behind the scene of deploying
>![2022-01-27](https://user-images.githubusercontent.com/92302123/151407328-88048d86-5c48-40d0-ac50-eb622bd8ef9c.png)
>![2022-01-27 (1)](https://user-images.githubusercontent.com/92302123/151407350-6b311591-60de-4601-83c8-e0d509aa7481.png)
## More on running functions than you want to know
> **Rule** : *We Want to change any data that gets stored on the blockchain, we are going to have to submit a transaction.*
>- And what's more, not only do we have to submit the transaction, but we also have to wait for it to be mined or to go through that proof of work algorithm, and that can take anywhere from 10 to 30 seconds execute.
> ![image](https://user-images.githubusercontent.com/92302123/151534682-014c7141-961e-4968-9efe-345c9f1573b8.png)
## Wei VS Ether
> 1 ether = 10^18 wei (1,000,000,000,000,000,000 wei)
## Gas Transaction
>“Gas refers to the unit that measures the amount of computational effort required to execute specific operations on the Ethereum network. Since each Ethereum transaction requires computational resources to execute, each transaction requires a fee.
> ![image](https://user-images.githubusercontent.com/92302123/151585596-d589bc97-2bae-4671-94be-85edaecd75c2.png)
## Mnemonic phrases
>![image](https://user-images.githubusercontent.com/92302123/151589264-21e34e71-6d31-419d-9211-7c53b1a11bf2.png)
> Mnemonic to public/private and address converter : https://iancoleman.io/bip39/
## Getting more test ether (0.1 ether in one request in Rinkenby account)
> https://faucets.chain.link/rinkeby

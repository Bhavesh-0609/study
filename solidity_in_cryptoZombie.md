# 2. Zombie attack their victime
## Chapter 7: Storage vs Memory (Data location)
>In Solidity, there are two locations you can store variables — in storage and in memory.
>
>Storage refers to variables stored permanently on the blockchain. Memory variables are temporary, and are erased between external function calls to your contract. Think of it like your computer's hard disk vs RAM.
>
>Most of the time you don't need to use these keywords because Solidity handles them by default. State variables (variables declared outside of functions) are by default storage and written permanently to the blockchain, while variables declared inside functions are memory and will disappear when the function call ends.
>
>However, there are times when you do need to use these keywords, namely when dealing with structs and arrays within functions:
```
contract SandwichFactory {
  struct Sandwich {
    string name;
    string status;
  }

  Sandwich[] sandwiches;

  function eatSandwich(uint _index) public {
    // Sandwich mySandwich = sandwiches[_index];

    // ^ Seems pretty straightforward, but solidity will give you a warning
    // telling you that you should explicitly declare `storage` or `memory` here.

    // So instead, you should declare with the `storage` keyword, like:
    Sandwich storage mySandwich = sandwiches[_index];
    // ...in which case `mySandwich` is a pointer to `sandwiches[_index]`
    // in storage, and...
    mySandwich.status = "Eaten!";
    // ...this will permanently change `sandwiches[_index]` on the blockchain.

    // If you just want a copy, you can use `memory`:
    Sandwich memory anotherSandwich = sandwiches[_index + 1];
    // ...in which case `anotherSandwich` will simply be a copy of the 
    // data in memory, and...
    anotherSandwich.status = "Eaten!";
    // ...will just modify the temporary variable and have no effect 
    // on `sandwiches[_index + 1]`. But you can do this:
    sandwiches[_index + 1] = anotherSandwich;
    // ...if you want to copy the changes back into blockchain storage.
  }
}
```
>Don't worry if you don't fully understand when to use which one yet — throughout this tutorial we'll tell you when to use storage and when to use memory, and the Solidity compiler will also give you warnings to let you know when you should be using one of these keywords.
>
>For now, it's enough to understand that there are cases where you'll need to explicitly declare storage or memory!

### Put it to the test
>It's time to give our zombies the ability to feed and multiply!
>
>When a zombie feeds on some other lifeform, its DNA will combine with the other lifeform's DNA to create a new zombie.
>
>Create a function called feedAndMultiply. It will take two parameters: _zombieId (a uint) and _targetDna (also a uint). This function should be public.
>
>We don't want to let someone else feed our zombie! So first, let's make sure we own this zombie. Add a require statement to verify that msg.sender is equal to this zombie's owner (similar to how we did in the createRandomZombie function).
>
>Note: Again, because our answer-checker is primitive, it's expecting msg.sender to come first and will mark it wrong if you switch the order. But normally when you're coding, you can use whichever order you prefer — both are correct.
>
>We're going to need to get this zombie's DNA. So the next thing our function should do is declare a local Zombie named myZombie (which will be a storage pointer). Set this variable to be equal to index _zombieId in our zombies array.
>
>You should have 4 lines of code so far, including the line with the closing }.
>
>We'll continue fleshing out this function in the next chapter!
```
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract ZombieFeeding is ZombieFactory {

  function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
  }

}
```
## Chapter 8: Zombie DNA
>Let's finish writing the feedAndMultiply function.
>
>The formula for calculating a new zombie's DNA is simple: the average between the feeding zombie's DNA and the target's DNA.
>
>For example:
```
function testDnaSplicing() public {
  uint zombieDna = 2222222222222222;
  uint targetDna = 4444444444444444;
  uint newZombieDna = (zombieDna + targetDna) / 2;
  // ^ will be equal to 3333333333333333
}
```
>Later we can make our formula more complicated if we want to, like adding some randomness to the new zombie's DNA. But for now we'll keep it simple — we can always come back to it later.

### Put it to the test
>First we need to make sure that _targetDna isn't longer than 16 digits. To do this, we can set _targetDna equal to _targetDna % dnaModulus to only take the last 16 digits.
>
>Next our function should declare a uint named newDna, and set it equal to the average of myZombie's DNA and _targetDna (as in the example above).
>
>Note: You can access the properties of myZombie using myZombie.name and myZombie.dna
>
>Once we have the new DNA, let's call _createZombie. You can look at the zombiefactory.sol tab if you forget which parameters this function needs to call it. Note that it requires a name, so let's set our new zombie's name to "NoName" for now — we can write a function to change zombies' names later.

>Note: For you Solidity whizzes, you may notice a problem with our code here! Don't worry, we'll fix this in the next chapter ;)
```
pragma solidity >=0.5.0 <0.6.0;

import "./zombiefactory.sol";

contract ZombieFeeding is ZombieFactory {

  function feedAndMultiply(uint _zombieId, uint _targetDna) public {
    require(msg.sender == zombieToOwner[_zombieId]);
    Zombie storage myZombie = zombies[_zombieId];
    _targetDna = _targetDna % dnaModulus;
    uint newDna = (myZombie.dna + _targetDna) / 2;
    _createZombie("NoName", newDna);
  }
}
```
## Chapter 9: More on Function Visibility
>The code in our previous lesson has a mistake!
>
>If you try compiling it, the compiler will throw an error.
>
>The issue is we tried calling the _createZombie function from within ZombieFeeding, but _createZombie is a private function inside ZombieFactory. This means none of the contracts that inherit from ZombieFactory can access it.
>
>Internal and External
>In addition to public and private, Solidity has two more types of visibility for functions: internal and external.
>
>internal is the same as private, except that it's also accessible to contracts that inherit from this contract. (Hey, that sounds like what we want here!).
>
>external is similar to public, except that these functions can ONLY be called outside the contract — they can't be called by other functions inside that contract. We'll talk about why you might want to use external vs public later.
>
>For declaring internal or external functions, the syntax is the same as private and public:
```
contract Sandwich {
  uint private sandwichesEaten = 0;

  function eat() internal {
    sandwichesEaten++;
  }
}

contract BLT is Sandwich {
  uint private baconSandwichesEaten = 0;

  function eatWithBacon() public returns (string memory) {
    baconSandwichesEaten++;
    // We can call this here because it's internal
    eat();
  }
}
```
### Put it to the test
>Change _createZombie() from private to internal so our other contract can access it.
>
>We've already focused you back to the proper tab, zombiefactory.sol.
```
pragma solidity >=0.5.0 <0.6.0;

contract ZombieFactory {

    event NewZombie(uint zombieId, string name, uint dna);

    uint dnaDigits = 16;
    uint dnaModulus = 10 ** dnaDigits;

    struct Zombie {
        string name;
        uint dna;
    }

    Zombie[] public zombies;

    mapping (uint => address) public zombieToOwner;
    mapping (address => uint) ownerZombieCount;

    // edit function definition below
    function _createZombie(string memory _name, uint _dna) internal {
        uint id = zombies.push(Zombie(_name, _dna)) - 1;
        zombieToOwner[id] = msg.sender;
        ownerZombieCount[msg.sender]++;
        emit NewZombie(id, _name, _dna);
    }

    function _generateRandomDna(string memory _str) private view returns (uint) {
        uint rand = uint(keccak256(abi.encodePacked(_str)));
        return rand % dnaModulus;
    }

    function createRandomZombie(string memory _name) public {
        require(ownerZombieCount[msg.sender] == 0);
        uint randDna = _generateRandomDna(_name);
        _createZombie(_name, randDna);
    }
}
```
## Chapter 10: What Do Zombies Eat? (Interacting with other contracts)
>It's time to feed our zombies! And what do zombies like to eat most?
>
>Well it just so happens that CryptoZombies love to eat...
>
>CryptoKitties! 😱😱😱
>
>(Yes, I'm serious 😆 )
>
>In order to do this we'll need to read the kittyDna from the CryptoKitties smart contract. We can do that because the CryptoKitties data is stored openly on the blockchain. >Isn't the blockchain cool?!
>
>Don't worry — our game isn't actually going to hurt anyone's CryptoKitty. We're only reading the CryptoKitties data, we're not able to actually delete it 😉
>
### Interacting with other contracts
>For our contract to talk to another contract on the blockchain that we don't own, first we need to define an interface.
>
>Let's look at a simple example. Say there was a contract on the blockchain that looked like this:
```
contract LuckyNumber {
  mapping(address => uint) numbers;

  function setNum(uint _num) public {
    numbers[msg.sender] = _num;
  }

  function getNum(address _myAddress) public view returns (uint) {
    return numbers[_myAddress];
  }
}
```

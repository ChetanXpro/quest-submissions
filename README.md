# quest-submissions

# CHAPTER-1 DAY-1


1.Explain what the Blockchain is in your own words...

-> Blockchain was first introduce by a unknown persion named Satoshi Nakamoto in 2008, blockchain is a open , permanent and distributed database which is      spread in  thousands of nodes.
   it is impossible to edit and delete the data on nodes, blockchain store data in chain of blocks and each block contain ledger of all transactions,
   participants can confirm transactions without permissions of central authority.
   usually Central authority can ban any user from their platform but in bloackchain there are no central authority, so users have no restrictions 
   
   
2. Explain what a Smart Contract is.
   
   -> Smart contracts are programs which run on blockchain , 
     A smart contract is a digital agreement that enables two or more parties to exchange money, Nfts etc in a conflict-free way while avoiding the               need for a third party they are enforced by a specific set of rules. These rules are predefined by computer code.
    
3.Explain the difference between a script and a transaction.
  
  -> A transaction can change the data on blockchain thats why it will cost money.
  -> A script can only view data on blockchain and thats why there is not charge for this.
  
  
  
  
 # CHAPTER-1 DAY-2
 
 
 1.What are the 5 Cadence Programming Language Pillars?
 
 - Safety and Security
 - Clarity
 - Approachability
 - Developer Experience
 - Resource Oriented Programming


2.In your opinion, even without knowing anything about the Blockchain or coding

- Safety/Security is the main priority of any language. 
- Clarity: there should be clarity in any language it should be readable , so that any user who dont know programming and atleast he got overview what is   hapnning.  
- approachability: A language should be in such a way that a programmer can realate things whith their prior experience.
- Developer Experience: debugging is the main part of programming, language should be easy to debug , this will save lots of time of devs.

- Resource Oriented Programming: As we know a small mistake in code can lead to million dollar loss , by the help of resources it can be hard for a    developer to made a mistake. this can restrict devs to make mistakes which can lead to major losses of some important nfs etc. 


# Chapter-2 Day 1


1.Deploy a contract to account 0x03 called "JacobTucker". Inside that contract, declare a constant variable named is, and make it have type String. Initialize it to "the best" when your contract gets deployed.

![contract](https://user-images.githubusercontent.com/107798155/189510226-ca5943b2-547f-4ea0-9623-2483208899d7.png)


2.Check that your variable is actually equals "the best" by executing a script to read that variable. Include a screenshot of the output.

![script](https://user-images.githubusercontent.com/107798155/189510337-5e13c872-7904-4911-a7cc-3988e8d3186d.png)


# Chapter-2 Day-2

1.Explain why we wouldn't call changeGreeting in a script.
 
 - because we can only view data with script , to call changeGreeting we have to use transaction.

2.What does the AuthAccount mean in the prepare phase of the transaction?

- AuthAccount is used to access data stored in that account, and it represent the account which sending the transaction.

3.What is the difference between the prepare phase and the execute phase in the transaction?

- In prepare phase we can access user data and can store data and can also execute functions 
- In execute phase we can only call functions we cant access user data.


4. Contract,Transaction,Script.

  ![contract](https://user-images.githubusercontent.com/107798155/189510988-e4ffb1b9-77cd-41c8-8197-b7a6a901b4e7.png)

  ![transaction](https://user-images.githubusercontent.com/107798155/189511021-1d34fa54-e9b4-43cc-a32b-72407593580d.png)
   
  ![script](https://user-images.githubusercontent.com/107798155/189511030-5a25082f-a88e-4c12-8def-e01eba3eb26c.png)
  

# Chapter-2 Day 3

1. In a script, initialize an array (that has length == 3) of your favourite people, represented as Strings, and log it.

- ![array](https://user-images.githubusercontent.com/107798155/193441697-40dfca55-b562-479d-a990-4f184141dc97.png)


2. In a script, initialize a dictionary that maps the Strings Facebook, Instagram, Twitter, YouTube, Reddit, and LinkedIn to a UInt64 that represents the order in which you use them from most to least. For example, YouTube --> 1, Reddit --> 2, etc. If you've never used one before, map it to 0!.

- ![dictionary](https://user-images.githubusercontent.com/107798155/193441724-e2294758-77b3-49c3-9564-f6227c6d2ac6.png)

3. Explain what the force unwrap operator ! does, with an example different from the one I showed you (you can just change the type).

- ! wll say if it is nill then panic and abort the program
- ! force cadence to not care about errors - like "i know what im doing, theres definitely something here"

- ![!](https://user-images.githubusercontent.com/107798155/193441727-e92847bc-df2b-4d9d-8771-53f89f73d3c3.png)

4. Using this picture below, explain...

  - What the error message means - Code is returning a String optional not a String.
  - Why we're getting this error -  because dictionaries return optinal values
  - How to fix it - Either force unwrap it ( Social[0x03]! ) or change the return type to be an optional ( pub fun main(): String? {} )
  
 - Error picture => <img width="1361" alt="wrongcode" src="https://user-images.githubusercontent.com/107798155/193442011-b81e5652-0749-40a7-8aa8-735566aba888.png">


# Chapter-2 Day 4

1. Deploy a new contract that has a Struct of your choosing inside of it (must be different than Profile).
2. Create a dictionary or array that contains the Struct you defined.
3. Create a function to add to that array/dictionary.

```
pub contract Cadence {
pub var mycats:{Address:Cats}
pub struct Cats{

pub var name:String
pub var age:Int


init(_name:String,_age:Int ){
self.name = _name
self.age = _age
}
}


pub fun addcats(name:String,age:Int,account:Address){

self.mycats[account] = Cats(_name:name,_age:age)

}

init(){

self.mycats = {}
}
}
```

4. Add a transaction to call that function in step 3.

```
import Cadence from 0x01

transaction(name:String,age:Int,account:Address){
prepare(signer:AuthAccount){}


execute{

Cadence.addcats(name: name, age: age, account: account)

}

}
```

5. Add a script to read the Struct you defined.

```
import Cadence from 0x01

pub fun main(account:Address): Cadence.Cats{
  return Cadence.mycats[account]!
}

```

# Chapter 3 Day 1 - Resources

1. In words, list 3 reasons why structs are different from resources.
  
  -  resources can't be copied but structs can be copied easily
  -  resources can't be lost, we can  intentionally destroy it.
  -  resources must be created and moved with very intentional, and there is  specific syntax to move resource.

2. Describe a situation where a resource might be better to use than a struct.

  - A resource is useful when the data is very valuable and it will be unique and needs to be carefully tracked, like a NFT.

3. What is the keyword to make a new resource?

  - create

4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

  - No, it has to be done in the contract.

5. What is the type of the resource below?

  ```
  pub resource Jacob {

  }
  ```
 - @Jacob

6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.
 
 Error code
 ```
 pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): Jacob { // there is 1 here
        let myJacob = Jacob() // there are 2 here
        return myJacob // there is 1 here
    }
}
 ```
 
 Correct code
 
 ```
 pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob { // added '@' to define resource type
        let myJacob <- create Jacob() // use move operator '<-' and 'create'
        return <- myJacob // use move operator '<-'
    }
}
 ```
 
 
# Chapter 3 Day 2 - Resources in Dictionaries & Arrays

1. Write your own smart contract that contains two state variables: an array of resources, and a dictionary of resources. Add functions to remove and add to each of them. They must be different from the examples above.

```
pub contract Meta{

pub var arrayOfMonkey: @[Monkey]
pub var dictionaryOfMonkey: @{String:ModernMonkey}

pub resource Monkey{

 pub var name:String

 init(){
 self.name = "FunnyMonkey"
 }
}

pub resource ModernMonkey{

 pub let name:String

 init(){
 self.name = "ChingChongMonkey"
 }
}

pub fun addMonkeyInArray(monkey:@Monkey){

 self.arrayOfMonkey.append(<- monkey)

}

pub fun removeMonkeyfromArray(id:UInt64):@Monkey{
 return <- self.arrayOfMonkey.remove(at: id)
}


pub fun addToDictionary(modernMonkey:@ModernMonkey){

 let key = modernMonkey.name

 self.dictionaryOfMonkey[key] <-! modernMonkey
}

pub fun removeFromDictionary(key:String):@ModernMonkey{

 let monkey <- self.dictionaryOfMonkey.remove(key: key) 
                   ?? panic("No resource at this key")

 return <- monkey

}

init(){
 self.arrayOfMonkey <- []
 self.dictionaryOfMonkey <- {}
 }
}
```
 
 
# Chapter 3 Day 3 - References

1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

 ```
  pub contract Meta{


pub var dictionaryOfMonkey: @{String:ModernMonkey}

pub resource ModernMonkey {

 pub let name:String


 init(){
 self.name = "Chetan"
 }
}

 
pub fun getref(name:String):&ModernMonkey?{

 return (&self.dictionaryOfMonkey[name] as &ModernMonkey?)?? panic("Nothing here")

}


init(){
 
 self.dictionaryOfMonkey <- {
  "MonkeyParty": <- create ModernMonkey()
        }
 }
}
 ```
2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

```
  import Meta from 0x01

pub fun main():&Meta.ModernMonkey{

 return (Meta.getref(name: "MonkeyParty")) ?? panic("Nothing here")
 
}

  ```

3. Explain, in your own words, why references can be useful in Cadence.

  - We dont have to move resources here and there, we can easily get refereces and then we can read and update data easily.


# Chapter 3 Day 4 - Resource/Struct Interfaces

1. Explain, in your own words, the 2 things resource interfaces can be used for (we went over both in today's content).
 
   - We can use resource interfaces when we want to expose certain function or informations to public and to restrict them to access private functions.
   - We can use resource interfaces to make sure  that our resources have certain functions and variables which are important.

2. Define your own contract. Make your own resource interface and a resource that implements the interface. Create 2 functions. In the 1st function, show    an example of not restricting the type of the resource and accessing its content. In the 2nd function, show an example of restricting the type of the    resource and NOT being able to access its content.

 ```
 pub contract Meta {

pub resource interface IMonkey {

 pub let name:String
    
}

pub resource Monkey:IMonkey {

  pub let name:String
 
  pub let number:Int

 init(){
  self.name = "Chetan"
  self.number = 4
 }

pub fun getname(){
 let myname:@Monkey <- create Monkey()
 log(myname.number)
 destroy myname
}

pub fun getname2(){
 
 let myname:@Monkey{IMonkey} <- create Monkey()

 log(myname.number)
  

 destroy myname

}    
}
}
 ```
 
3. How would we fix this code?
 
 Bad code - 
 
  ```
 pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
    }

    // ERROR:
    // `structure Stuff.Test does not conform 
    // to structure interface Stuff.ITest`
    pub struct Test: ITest {
      pub var greeting: String

      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting // returns the new greeting
      }

      init() {
        self.greeting = "Hello!"
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") // ERROR HERE: `member of restricted type is not accessible: changeGreeting`
      log(newGreeting)
    }
} 
  ```
  
  
  Correct code - 
  
  ```
  pub contract Stuff {

    pub struct interface ITest {
      pub var greeting: String
      pub var favouriteFruit: String
      pub fun changeGreeting(newGreeting: String): String  // We have to add function in resource interface so that we can call that resource func in                                                                //function in which we applying interface 
    }

   
    pub struct Test: ITest {
      pub var greeting: String

      pub var favouriteFruit:String // We have to add favouriteFruit variable because it is defined in interface
      pub fun changeGreeting(newGreeting: String): String {
        self.greeting = newGreeting
        return self.greeting 
      }

      init() {
        self.greeting = "Hello!"
        self.favouriteFruit = "apple"
      }
    }

    pub fun fixThis() {
      let test: Test{ITest} = Test()
      let newGreeting = test.changeGreeting(newGreeting: "Bonjour!") 
      log(newGreeting)
    }
}
  ```


#  Chapter 3 Day 5 - Access Control

1. For today's quest, you will be looking at a contract and a script. You will be looking at 4 variables (a, b, c, d) and 3 functions (publicFunc,         contractFunc, privateFunc) defined in SomeContract. In each AREA (1, 2, 3, and 4), I want you to do the following: for each variable (a, b, c, and d),   tell me in which areas they can be read (read scope) and which areas they can be modified (write scope). For each function (publicFunc, contractFunc,     and privateFunc), simply tell me where they can be called.  

 ```
 access(all) contract SomeContract {
    pub var testStruct: SomeStruct

    pub struct SomeStruct {

        //
        // 4 Variables
        //

        pub(set) var a: String

        pub var b: String

        access(contract) var c: String

        access(self) var d: String

        //
        // 3 Functions
        //

        pub fun publicFunc() {}

        access(contract) fun contractFunc() {}

        access(self) fun privateFunc() {}


        pub fun structFunc() {
            /**************/
            /*** AREA 1 ***/
            /**************/
            
        A -> We can Read & Write
        B -> We can Read & Write
        C -> We can Read & Write
        D -> We can Read & Write
        }

        init() {
            self.a = "a"
            self.b = "b"
            self.c = "c"
            self.d = "d"
        }
    }

    pub resource SomeResource {
        pub var e: Int

        pub fun resourceFunc() {
            /**************/
            /*** AREA 2 ***/
            /**************/
            A -> We can Read & Write
            B -> Only Read
            C -> Only Read
            D -> We cant read and Write
        }

        init() {
            self.e = 17
        }
    }

    pub fun createSomeResource(): @SomeResource {
        return <- create SomeResource()
    }

    pub fun questsAreFun() {
        /**************/
        /*** AREA 3 ****/
        /**************/
        A -> We can Read & Write
        B -> Only Read
        C -> Only Read
        D -> We cant read and Write
        
        We can call public and contract Function
    }

    init() {
        self.testStruct = SomeStruct()
    }
}
 ```
 
 Script
 
  ```
  import SomeContract from 0x01

pub fun main() {
  /**************/
  /*** AREA 4 ***/
  /**************/
  
  A -> We can read
  B -> We can read
  
     Public function
  
}
  ```
  
  
# Chapter 4 Day 1 - Account Storage

1. Explain what lives inside of an account.

  - Account storage which can contain our nft etc
  - Smart contract, a account can have multiple contracts

2. What is the difference between the /storage/, /public/, and /private/ paths?

   - Storage  -> everything is stored in account storage and only owner can access storage.
   -  public and private are paths 
   -  Public -> Owner can link some data to public path so that everyone can see that like nft and nft deposit func.
   -  Private -> Owner can give access to some peoples to access certain data and only those people can access that data

3. What does .save() do? What does .load() do? What does .borrow() do ?

   - .save() -> We can save resources etc in our storage on certain path like /storage/Nft
  
   - .load() -> We can get data from our storage and then we can some stuff with data.
  
   - .borrow() -> We can borrow data directly from storage and we don't have to load our data from storage and then save it back. We can directly get                      reference to resource etc and then we can read that.
 

4. Explain why we couldn't save something to our account storage inside of a script.

   - We can only save something to our storage in transaction prepare phase , only signer is authorized to access their storage, and in script we can         only view data.

5. Explain why I couldn't save something to your account.

   - You dont have my auth account access  
   - Each signer can only save to their own storage.


6. Define a contract that returns a resource that has at least 1 field in it. Then, write 2 transactions:

   i. A transaction that first saves the resource to account storage, then loads it out of account storage, logs a field inside the resource, and               destroys it.

   ii. A transaction that first saves the resource to account storage, then borrows a reference to it, and logs a field inside the resource.


  - Contract
  
  ```
   pub contract Zolo {

    pub resource NFT {

    pub let name:String

    init(_name:String){
     self.name = _name
    }
    
   }

   pub fun mint(name:String):@NFT{

     return <- create NFT(_name:name)

     } 


     }
  ```
  - Transaction i

```
import Zolo from 0x01

transaction(name:String){

prepare(signer:AuthAccount){


let mynft <- Zolo.mint(name: name)

signer.save(<- mynft, to: /storage/mynft)

let again <- signer.load<@Zolo.NFT>(from: /storage/mynft) ?? panic("Nothing here")

log(again.name)

destroy again

}

}

```

  - Transaction ii

```
import Zolo from 0x01

transaction(name:String){

prepare(signer:AuthAccount){


let mynft <- Zolo.mint(name: name)

signer.save(<- mynft, to: /storage/mynft)

let nft = signer.borrow<&Zolo.NFT>(from: /storage/mynft) ?? panic("Nothing here")

log(nft.name)

}
}

```

# Chapter 4 Day 2 - Capabilities
 
1. What does .link() do ?

  - We can link some data from storage to public or private path.

2. In your own words (no code), explain how we can use resource interfaces to only expose certain things to the /public/ path.

  - If we have some important function in our resource like to withdraw an NFT, and when we link our resource to public path then anyone can call it and     withdraw nft, 
  - BUT  if we use resource interface then we can limit people to only read nft name and some more details which we want to show them.

3. Deploy a contract that contains a resource that implements a resource interface. Then, do the following:

   i. In a transaction, save the resource to storage and link it to the public with the restrictive interface.

   ii. Run a script that tries to access a non-exposed field in the resource interface, and see the error pop up.

   iii. Run the script and access something you CAN read from. Return it from the script.
   

 - Contract 

  ```
  pub contract Zolo {


    pub resource interface INFT {

      pub name:String
    
    }

    pub resource NFT:INFT {

     pub var name:String

     pub fun changename(newname:String){
       self.name = newname
     }

     init(_name:String){
      self.name = _name
     }
    
   }

   pub fun mint(name:String):@NFT{

    return <- create NFT(_name:name)

   } 


  }
  
  ```
  
i. Transaction 

```
import Zolo from 0x01

transaction(name:String){

prepare(signer:AuthAccount){


let mynft <- Zolo.mint(name: name)

signer.save(<- mynft, to: /storage/mynft)

signer.link<&Zolo.NFT{Zolo.INFT}>(/public/mynft, target: /storage/mynft) ?? panic("Nothing to link")


}

}
```
ii. Script 

```
import Zolo from 0x01

pub fun main(){

let my = getAccount(0x01).getCapability<&Zolo.NFT{Zolo.INFT}>(/public/mynft)

let test = my.borrow() ?? panic("Nothing here")

test.changename(newname: "hi") // ERROR : // member of restricted type is not accessible:changename

}


```

 iii. Script 
 
 ```
 import Zolo from 0x01

pub fun main():String{

let my = getAccount(0x01).getCapability<&Zolo.NFT{Zolo.INFT}>(/public/mynft)

let test = my.borrow() ?? panic("Nothing here")

return test.name

}

 
 ```
 
 
# Chapter 4 Day 3 - Creating an NFT Contract: Collections (Part 1/3)
 
 
1. Why did we add a Collection to this contract? List the two main reasons.

  - With collection we can store multiple resource on single path
  - And we can put multiple methods lke to deposit or withdraw nft.

2. What do you have to do if you have resources "nested" inside of another resource? ("Nested resources")

  - We have to define a destory function to destroy these nested resources manually.

3. Brainstorm some extra things we may want to add to this contract. Think about what might be problematic with this contract and how we could fix it.

    Idea #1: Do we really want everyone to be able to mint an NFT? thinking.
         - No we dont want to allow anyone to mint us an NFT, We can allow createNFT function for admin only.

    Idea #2: If we want to read information about our NFTs inside our Collection, right now we have to take it out of the Collection to do so. Is this g              Good?
     
     - We could add a function which will give us reference to our NFT. 
 
  

# Chapter 4 Day 4 - Creating an NFT Contract: Transferring, Minting, and Borrowing (Part 2/3)

 1. Take our NFT contract so far and add comments to every single resource or function explaining what it's doing in your own words. Something like this:

 ```
 pub contract CryptoPoops {
  pub var totalSupply: UInt64

  // This is an NFT resource that contains a name,
  // favouriteFood, and luckyNumber
  pub resource NFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

  // This is a resource interface that allows us to restrict public to use certain important functions like withdraw etc
  // We have to give  this interface type when we link collection to public path.
  // Public can only access functions which are availabe in this interface

  pub resource interface CollectionPublic {
    pub fun deposit(token: @NFT)
    pub fun getIDs(): [UInt64]
    pub fun borrowNFT(id: UInt64): &NFT
  }

  // we create this resource so that we can store our All NFTS and functions in one storage path
  // by creating this resource we can easily access Map our nft to nft ids

  pub resource Collection: CollectionPublic {
    pub var ownedNFTs: @{UInt64: NFT}

    // This function will desposit nft in our collection that is ownedNFTs dictionary

    pub fun deposit(token: @NFT) {
      self.ownedNFTs[token.id] <-! token
    }
    
    // Whit this withdraw function we can easily withdraw NFT from  ownedNFTs

    pub fun withdraw(withdrawID: UInt64): @NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
              ?? panic("This NFT does not exist in this Collection.")
      return <- nft
    }
    
    // With this function we will get all nft ids which are present in our collection.

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }
  
     // With this function we can get our nft metadata , its all details like name etc
     // Basically we are creating a reference

    pub fun borrowNFT(id: UInt64): &NFT {
      return (&self.ownedNFTs[id] as &NFT?)!
    }

    init() {
      self.ownedNFTs <- {}
    }

    // When resources are nested inside another resource then we have to define a destroy 
    // function to destory nested resources manually

    destroy() {
      destroy self.ownedNFTs
    }
  }

  // This function will create an empty collection inside signer storage
  // And now signer can get NFT and he will get access to other functions of collection resource

  pub fun createEmptyCollection(): @Collection {
    return <- create Collection()
  }

  // We have to define a Minter resource so that only persion Who have this resource can Mint an NFT
  // One who deployed this contract will get access to mint nft coz we create this resource in contract init

  pub resource Minter {
     
     // Function to mint nft
    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    //By this function owner can give minter resource to other account
    // and then he can also mint nft

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }
   
   // Here we defining totalsupply
   // we also saving minter resource to contract owner account
  init() {
    self.totalSupply = 0
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
 ```





# Chapter 5 Day 1 - Pre/Post Conditions & Events

1. Describe what an event is, and why it might be useful to a client.

 - When we define a event and then emit it , it will broadcast it on blockchain
 - For example if we emit an event in a mint function and transfer function , every time someone mint an NFT event will broadcast it on blockchain
 - We can also use emitted messages in our frontend.
 - It will also a cheaper solution to get info in our frontend

2. Deploy a contract with an event in it, and emit the event somewhere else in the contract indicating that it happened.

```
pub contract YUP{

pub event favFruit(fruit:String)
pub event favFruitChanged(from:String,to:String)


pub var myfavFruit:String


pub fun changeFavFruit(fruit:String){

emit favFruitChanged(from:self.myfavFruit,to:fruit)

self.myfavFruit = fruit
}

init(){
 self.myfavFruit = "DevilFruit"
 emit favFruit(fruit:self.myfavFruit)
}

}
```

3. Using the contract in step 2), add some pre conditions and post conditions to your contract to get used to writing them out.

```
pub contract YUP{

pub event favFruit(fruit:String)
pub event favFruitChanged(from:String,to:String)

pub var limit:UInt64
pub var namechangeCount:UInt64

pub var myfavFruit:String


pub fun changeFavFruit(fruit:String){

pre {
  fruit != "Apple" : "You should eat banana or something else  ok?"
}

post {
  self.limit > self.namechangeCount:"You cant change your name anymore"
}

emit favFruitChanged(from:self.myfavFruit,to:fruit)
self.namechangeCount = self.namechangeCount + 1
self.myfavFruit = fruit
}

init(){
 self.myfavFruit = "DevilFruit"
 emit favFruit(fruit:self.myfavFruit)
 self.limit = 5
 self.namechangeCount = 0
}

}
```

4. For each of the functions below (numberOne, numberTwo, numberThree), follow the instructions.
    
    - Number One -> It will log the name. (pre clear)
    - Number Two -> It will not return value (Post fail)
    - Number Three -> No it will not log number (Before value is 0 and then it add 1 to it thats why it will fail post condition)
 
 ```
 pub contract Test {

  // TODO
  // Tell me whether or not this function will log the name.
  // name: 'Jacob'
  pub fun numberOne(name: String) {
    pre {
      name.length == 5: "This name is not cool enough."
    }
    log(name)
  }

  // TODO
  // Tell me whether or not this function will return a value.
  // name: 'Jacob'
  pub fun numberTwo(name: String): String {
    pre {
      name.length >= 0: "You must input a valid name."
    }
    post {
      result == "Jacob Tucker"
    }
    return name.concat(" Tucker")
  }

  pub resource TestResource {
    pub var number: Int

    // TODO
    // Tell me whether or not this function will log the updated number.
    // Also, tell me the value of `self.number` after it's run.
    pub fun numberThree(): Int {
      post {
        before(self.number) == result + 1
      }
      self.number = self.number + 1
      return self.number
    }

    init() {
      self.number = 0
    }

  }

}
 
 ```
 
 
# Chapter 5 Day 2 - Contract Interfaces


1. Explain why standards can be beneficial to the Flow ecosystem. 
  
  - By implementing Standards we know there will be certain functions , and without looking at code we know that nft smart contract will have these         functions and variables , like it will have withdraw function and it will take a id parameter.
  - we can intract with contracts easily.
  - And also standards will give some security, like we cant do much in withdraw func and trick user.

2. What is YOUR favourite food ?

  - Simple daal & roti  btw its indian food


3. Please fix this code (Hint: There are two things wrong):

  i.The contract interface:
  
  ```
  pub contract interface ITest {
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    pre {
      newNumber >= 0: "We don't like negative numbers for some reason. We're mean."
    }
    post {
      self.number == newNumber: "Didn't update the number to be the new number."
    }
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff {
    pub var favouriteActivity: String
  }
}
  
  ```
  
  ii. The implementing contract:
  
  ```
  // We have to import interface contract
  import ITest from 0x02
  pub contract Test { // We have to add :ITest to implement contract interface.
  pub var number: Int
  
  pub fun updateNumber(newNumber: Int) {
    self.number = 5
  }

  pub resource interface IStuff {
    pub var favouriteActivity: String
  }

  pub resource Stuff: IStuff { // We have to add ITest.IStuff 
    pub var favouriteActivity: String

    init() {
      self.favouriteActivity = "Playing League of Legends."
    }
  }

  init() {
    self.number = 0
  }
}
  ```

# Chapter 5 Day 3 - Creating an NFT Contract: Implementing the NonFungibleToken Standard (Part 3/3)
 

 1. What does "force casting" with as! do? Why is it useful in our Collection?

   - as! will downcast to more specific type from generic type , it will make sure no one can deposit there own NFT type And only they can deposit our        NFT type
  

 2. What does auth do? When do we use it?

   - When we have to downcast reference we have to use auth and authorsied the reference.In our NFT contract borrow function we are getting                  &NonFungibleToken.NFT reference but &NonFungibleToken.NFT expose only id so we need more specific reference to &NFT, so in this case we have to use
     authorsied reference to downcast.
     
     
 3. This last quest will be your most difficult yet. Take this contract:

  - Contract

   ```
   import NonFungibleToken from 0x02

pub contract CryptoPoops: NonFungibleToken {
  pub var totalSupply: UInt64

  pub event ContractInitialized()
  pub event Withdraw(id: UInt64, from: Address?)
  pub event Deposit(id: UInt64, to: Address?)

  pub resource NFT: NonFungibleToken.INFT {
    pub let id: UInt64

    pub let name: String
    pub let favouriteFood: String
    pub let luckyNumber: Int

    init(_name: String, _favouriteFood: String, _luckyNumber: Int) {
      self.id = self.uuid

      self.name = _name
      self.favouriteFood = _favouriteFood
      self.luckyNumber = _luckyNumber
    }
  }

    pub resource interface CollectionPublic {
        pub fun deposit(token: @NonFungibleToken.NFT)
        pub fun getIDs(): [UInt64]
        pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT
        pub fun borrowAuthNFT(id: UInt64): &NFT
    }
 
  pub resource Collection: NonFungibleToken.Provider, NonFungibleToken.Receiver, NonFungibleToken.CollectionPublic,CollectionPublic {
    pub var ownedNFTs: @{UInt64: NonFungibleToken.NFT}

    pub fun withdraw(withdrawID: UInt64): @NonFungibleToken.NFT {
      let nft <- self.ownedNFTs.remove(key: withdrawID) 
            ?? panic("This NFT does not exist in this Collection.")
      emit Withdraw(id: nft.id, from: self.owner?.address)
      return <- nft
    }

    pub fun deposit(token: @NonFungibleToken.NFT) {
      let nft <- token as! @NFT
      emit Deposit(id: nft.id, to: self.owner?.address)
      self.ownedNFTs[nft.id] <-! nft
    }

    pub fun getIDs(): [UInt64] {
      return self.ownedNFTs.keys
    }

    pub fun borrowAuthNFT(id:UInt64):&NFT{
    let reference = (&self.ownedNFTs[id] as auth &NonFungibleToken.NFT?)!
    
    return reference as! &NFT
    }

    pub fun borrowNFT(id: UInt64): &NonFungibleToken.NFT {
      return (&self.ownedNFTs[id] as &NonFungibleToken.NFT?)!
    }

    init() {
      self.ownedNFTs <- {}
    }

    destroy() {
      destroy self.ownedNFTs
    }
  }

  pub fun createEmptyCollection(): @NonFungibleToken.Collection {
    return <- create Collection()
  }

  pub resource Minter {

    pub fun createNFT(name: String, favouriteFood: String, luckyNumber: Int): @NFT {
      return <- create NFT(_name: name, _favouriteFood: favouriteFood, _luckyNumber: luckyNumber)
    }

    pub fun createMinter(): @Minter {
      return <- create Minter()
    }

  }

  init() {
    self.totalSupply = 0
    emit ContractInitialized()
    self.account.save(<- create Minter(), to: /storage/Minter)
  }
}
   
   ```


 - Creating collection in storage and link it in public path with interface.

 ```
 import CryptoPoops from 0x03
import NonFungibleToken from 0x02

transaction(){

prepare(signer:AuthAccount){

signer.save( <- CryptoPoops.createEmptyCollection(), to: /storage/myCollection)

signer.link<&CryptoPoops.Collection{NonFungibleToken.CollectionPublic,NonFungibleToken.Receiver, CryptoPoops.CollectionPublic}>(/public/myCollection, target: /storage/myCollection) 
                  ?? panic("Nothing to link")
}

}
 
 ```
 
 - Minting an NFT

```

import CryptoPoops from 0x03

transaction(recipientAddress:Address){

prepare(signer:AuthAccount){


let minter = signer.borrow<&CryptoPoops.Minter>(from: /storage/Minter) ?? panic("Signer dont have minter resource")

 let recipientsCollection = getAccount(recipientAddress).getCapability(/public/myCollection).borrow<&CryptoPoops.Collection{CryptoPoops.CollectionPublic}>() 
                             ?? panic("No public path")

recipientsCollection.deposit(token: <- minter.createNFT(name: "haha",favouriteFood:"DEVIL FRUIT",luckyNumber:69))
 
}
execute{
log("NFT Minted")
}
}
```

- Get account all nft ids so that we can read metadata with nft id in script.

```
import CryptoPoops from 0x03

transaction(account:Address) {

prepare(signer:AuthAccount){

let ref = getAccount(account).getCapability(/public/myCollection).borrow<&CryptoPoops.Collection{CryptoPoops.CollectionPublic}>()
                                        ?? panic("Nothng")

 log(ref.getIDs())

}
}

```

- Script to read nft metadata

```
import CryptoPoops from 0x03

pub fun main(account:Address,id:UInt64){

let nft = getAccount(account).getCapability(/public/myCollection).borrow<&CryptoPoops.Collection{CryptoPoops.CollectionPublic}>()
                                  ?? panic("No nft")


let ref = nft.borrowNFT(id: id)

log(ref)


}


```


# Chapter 6 Day 1 - Creating a Testnet Account & Deploying to Testnet


1. Go to https://flow-view-source.com/testnet/. Where it says "Account", paste in the Flow address you generated and click "Go". On the left hand side,    you should see your NFT contract. Isn't it so cool to see it live on Testnet? Then, send the URL to the page.

- MY ACCOUNT LINK -> https://flow-view-source.com/testnet/account/0x41fc5dad4ffbd005/


# Chapter 6 Day 2 - Interacting With Our Contract on Testnet.


1. Figure out how to mint an NFT to yourself by sending a transaction using the Flow CLI, like we did today when we set up our collection. You will also    likely have to pass an argument as well.

 - Command -> flow transactions send ./cadence/transactions/MintNFT.cdc 0x41fc5dad4ffbd005 --network=testnet --signer=testnet-account
 
 - Signed Transaction ✅

  ![MintNFT](https://user-images.githubusercontent.com/107798155/194112567-91f22838-d866-49c5-9347-76c4f23b1650.png)
  
2. Run a script to read the new totalSupply using the Flow CLI

  - Command -> flow scripts execute ./cadence/scripts/TotalSupply.cdc --network=testnet

  ![Totalsupply](https://user-images.githubusercontent.com/107798155/194113494-51a40aa7-6965-4c56-a6b1-e406eb01ec2d.png)

  

3. Run a script to read the ids of NFTs in someone's collection using the Flow CLI.

  - Command -> flow scripts execute ./cadence/scripts/GetIds.cdc 0x41fc5dad4ffbd005 --network=testnet

  ![GetIds](https://user-images.githubusercontent.com/107798155/194115025-78890ce1-27a7-4636-9d71-dcbc28c3b730.png)
  
  
4. Run a script to read a specific NFT's metadata from someone's collection using the Flow CLI.

 - Command -> flow scripts execute ./cadence/scripts/GetMetadata.cdc 0x41fc5dad4ffbd005 112296266  --network=testnet

 ![Getmetadata](https://user-images.githubusercontent.com/107798155/194116130-5eb5d23e-c266-4297-a862-116cd7e9adaf.png)
 
 
5. Run a script to read the GoatedGoats totalSupply on Flow Mainnet. Their contract lives here: https://flow-view-                                          source.com/mainnet/account/0x2068315349bdfce5/contract/GoatedGoats

 - Command ->  flow scripts execute ./cadence/scripts/TotalSupply.cdc --network=mainnet
 - Totalsuppy of GoatedGoats : 18477
 

![Goat](https://user-images.githubusercontent.com/107798155/194117449-c3f50bdc-30d4-4110-96b4-89891e7ab8d0.png)


6. Figure out how to read someone's GoatedGoats NFTs from their collection and run a script using the Flow CLI to do it.

 - Command ->  flow scripts execute ./cadence/scripts/GetIds.cdc (Address)  --network=mainnet
 
  ```
  import GoatedGoats from 0x2068315349bdfce5

  pub fun main(account:Address):[UInt64]{

   let ref = getAccount(account).getCapability(/public/GoatCollection).borrow<&GoatedGoats.Collection{GoatedGoats.GoatCollectionPublic}>()
   ?? panic("No colection in this account")

   return ref.getIDs()
 
   }
  ```


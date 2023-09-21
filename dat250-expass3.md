# Dat250-expass3

## Installation and verification of mongodb

1. Downloaded the MongoDB 4.4 Community Edition installation file
`curl -LO https://fastdl.mongodb.org/osx/mongodb-macos-x86_64-4.4.24.tgz`
2. Download the SHA256 file
`curl -LO https://fastdl.mongodb.org/osx/mongodb-macos-x86_64-4.4.24.tgz.sha256`
3. Use the SHA-256 checksum to verify the MongoDB package file
4. Check checksum: `shasum -c mongodb-macos-x86_64-4.4.24.tgz.sha256`

![download/var](/screenshots/download:verification.png)

As im on macOS, a simple `brew install mongodb-community@4.4`. Then add to $PATH. This includes the following binaries:
- The mongod server
- The mongos sharded cluster query router
- The mongo shell

## Running MongoDB

As a macOS service using brew:
- start: `brew services start mongodb-community@4.4`
- verify its running: `brew services list`
- begin using: `mongo`
- stop: `brew services stop mongodb-community@4.4`

## Experiment 1
- No issues running mongo and interacting with CRUD operations through the shell.
![exp1](/screenshots/exp1-insert.png)

## Experiment 2
- Running the premade map-reduce functions:
![map-reduce1](/screenshots/exp2-mr1.png)
![map-reduce2](/screenshots/exp2-mr2.png)

- Custom implemented Map-reduce operation:
    - I tried implementing my own map-reduce operations to find the most purchaced product by each customer. This could be useful for a store to create personalized discounts and deals

    - Unfortunally I have not made it work yet, having lots of fun working with javascripts `undefined`s :slightly_smiling_face:

```
var mapFunction3 = function() {
    emit(this.cust_id, this.items);
};

var reduceFunction3 = function(keyCust, valItems) {
   reducedVal = valItems[0].sku;
   largest = valItems[0].qty;
   
   for (var item = 0; item < valItems.length; item++) {
       if (valItems[item].qty >= largest) {
            reducedVal = valItems[item].sku
            largest = valItems[item].qty
       }
   }

   return reducedVal;
};

db.orders.mapReduce(
   mapFunction3,
   reduceFunction3,
   { out: "map_reduce_example3" }
)

```
 
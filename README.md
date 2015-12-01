# Simple MongoDB CRUD Sample

My repo to share what I've been learning on MongoDB studies :)

## C (create)

```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> db.family.insert({name:'Steve', relation: 'son'})
Inserted 1 record(s) in 264ms
WriteResult({
  "nInserted": 1
})

```
## R (read)

Without parameters

```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> db.private.find()
Fetched 0 record(s) in 0ms
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> db.family.find()
{
  "_id": ObjectId("565d2b9b495934b959882cce"),
  "name": "Steve",
  "relation": "son"
}
Fetched 1 record(s) in 1ms

```

With parameters

```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> db.family.find({name:'Steve'})
{
  "_id": ObjectId("565d2b9b495934b959882cce"),
  "name": "Steve",
  "relation": "son"
}
Fetched 1 record(s) in 1ms
```

## U (update)

1. Creating a variable to store the Steve object
```
var steve = db.family.findOne({name:'Steve'})
```

2. Showing the content of variable
```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> steve
{
  "_id": ObjectId("565d2b9b495934b959882cce"),
  "name": "Steve",
  "relation": "son"
}
```

3. Changing variable value

```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> steve.name = 'Steve Gomes'
Steve Gomes
```

4. Checking the changed effect before save

```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> steve
{
  "_id": ObjectId("565d2b9b495934b959882cce"),
  "name": "Steve Gomes",
  "relation": "son"
}
```

5. Change value again, adding keys to Json document
```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> steve.age = 3
3
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> steve
{
  "_id": ObjectId("565d2b9b495934b959882cce"),
  "name": "Steve Gomes",
  "relation": "son",
  "age": 3
}

```


6. Persinting permanetly changes

```
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> db.family.save(steve)
Updated 1 existing record(s) in 1ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
```

7. Querying all jsons doccuments from *Family* collection 
janynne-Lenovo-Ideapad-Flex14(mongod-3.0.7) private> db.family.find()
{
  "_id": ObjectId("565d2b9b495934b959882cce"),
  "name": "Steve Gomes",
  "relation": "son",
  "age": 3
}
Fetched 1 record(s) in 1ms

```

## D (delete)

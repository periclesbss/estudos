# MongoDB - Aula 03 - Exercício
autor: Péricles B S Santos

## Liste todos os Pokemons com a altura menor que 0.5
```
VM05(mongod-3.6.3) be-mean-instagram> var query = {height: {$lt: 0.5}};
VM05(mongod-3.6.3) be-mean-instagram> query;
{
  "height": {
    "$lt": 0.5
  }
}
VM05(mongod-3.6.3) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("5bc6c472f70a32c68c06e70b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attach": 55,
  "height": 0.4
}
{
  "_id": ObjectId("5bc6c590f70a32c68c06e70c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5bc7bb4a8c93a910e3567d75"),
  "name": "Caterpie",
  "description": "Larva lutadora",
  "type": "inseto",
  "attack": 30,
  "height": 0.3,
  "defense": 35
}
Fetched 3 record(s) in 780ms
VM05(mongod-3.6.3) be-mean-instagram> 
```

## Liste todos os Pokemons com a altura maior ou igual que 0.5
```
VM05(mongod-3.6.3) be-mean-instagram> var query = {height: {$gte: 0.5}};
VM05(mongod-3.6.3) be-mean-instagram> query;
{
  "height": {
    "$gte": 0.5
  }
}
VM05(mongod-3.6.3) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("5bc6c590f70a32c68c06e70d"),
  "name": "Charmander",
  "description": "Esse é o cão chupando manga de fofinho",
  "type": "fogo",
  "attack": 52,
  "height": 0.6
}
{
  "_id": ObjectId("5bc6c590f70a32c68c06e70e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
{
  "_id": ObjectId("5bc82e28af43ca396d968cd9"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": 8001,
  "defense": 8000,
  "height": 1.69
}
{
  "_id": ObjectId("5bc82e28af43ca396d968cda"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "besta",
  "attack": 1,
  "defense": 1,
  "height": 1.6
}
{
  "_id": ObjectId("5bc82e28af43ca396d968cdb"),
  "name": "Cunhamon",
  "description": "Filho da puta",
  "type": "beta",
  "attack": 9990,
  "defense": 9999,
  "height": 1.8
}
{
  "_id": ObjectId("5bc82e28af43ca396d968cdc"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da PUTA",
  "type": "besta",
  "attack": 8500,
  "defense": 9999,
  "height": 1.79
}
{
  "_id": ObjectId("5bc82e28af43ca396d968cdd"),
  "name": "FeliciANUS",
  "description": "Pastor baitola",
  "type": "besta",
  "attack": 666,
  "defense": 666,
  "height": 1.7
}
Fetched 7 record(s) in 25ms
VM05(mongod-3.6.3) be-mean-instagram> 
```

## Liste todos os Pokemons com a altura menor ou igual que 0.5 e do tipo grama
```
var query = {$and: [{height: {$lte: 0.5}}, {type: 'grama'}]};
var query = {$and: [{height: {$lte: 0.5}}, {type: "grama"}]};
var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]};

VM05(mongod-3.6.3) be-mean-instagram> var query = {$and: [{height: {$lte: 0.5}}, {type: /grama/}]};
VM05(mongod-3.6.3) be-mean-instagram> query;
{
  "$and": [
    {
      "height": {
        "$lte": 0.5
      }
    },
    {
      "type": /grama/
    }
  ]
}
VM05(mongod-3.6.3) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("5bc6c590f70a32c68c06e70c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
Fetched 1 record(s) in 5ms
VM05(mongod-3.6.3) be-mean-instagram> 
```

## Liste todos os Pokemons com o name 'Pikachu' ou com attack menor ou igual que 0.5
```
var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]}; --parâmetro "i" corresponde a insensitivo.

VM05(mongod-3.6.3) be-mean-instagram> var query = {$or: [{attack: {$lte: 0.5}}, {name: /pikachu/i}]};
VM05(mongod-3.6.3) be-mean-instagram> query;
{
  "$or": [
    {
      "attack": {
        "$lte": 0.5
      }
    },
    {
      "name": /pikachu/i
    }
  ]
}
VM05(mongod-3.6.3) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("5bc6c472f70a32c68c06e70b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attach": 55,
  "height": 0.4
}
Fetched 1 record(s) in 1ms
VM05(mongod-3.6.3) be-mean-instagram> 
```

## Liste todos os Pokemons com o attack maior ou igual que 48 e com height menor ou igual que 0.5
```
var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]};

VM05(mongod-3.6.3) be-mean-instagram> db.pokemons.find({name: 'Pikachu'}); --Pikachu não retornou devido a um erro sutil no nome "attach" vs "attack"
{
  "_id": ObjectId("5bc6c472f70a32c68c06e70b"),
  "name": "Pikachu",
  "description": "Rato elétrico bem fofinho",
  "type": "electric",
  "attach": 55,
  "height": 0.4
}
Fetched 1 record(s) in 3ms
VM05(mongod-3.6.3) be-mean-instagram> var query = {$and: [{attack: {$gte: 48}}, {height: {$lte: 0.5}}]};
VM05(mongod-3.6.3) be-mean-instagram> db.pokemons.find(query);
{
  "_id": ObjectId("5bc6c590f70a32c68c06e70c"),
  "name": "Bulbassauro",
  "description": "Chicote de trepadeira",
  "type": "grama",
  "attack": 49,
  "height": 0.4
}
{
  "_id": ObjectId("5bc6c590f70a32c68c06e70e"),
  "name": "Squirtle",
  "description": "Ejeta água que passarinho não bebe",
  "type": "água",
  "attack": 48,
  "height": 0.5
}
Fetched 2 record(s) in 3ms
VM05(mongod-3.6.3) be-mean-instagram> 

```
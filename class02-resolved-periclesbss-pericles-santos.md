# MongoDB - Aula 02 - Exercício
autor: Péricles B S Santos

## Crie um database chamada de be-mean-pokemons (passo 1)
```
VM05(mongod-3.6.3) test> use be-mean-pokemons;
switched to db be-mean-pokemons
```

## Liste quais databases você possui nesse servidor (passo 2)

```
VM05(mongod-3.6.3) be-mean-pokemons> show dbs;
admin             → 0.000GB
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
config            → 0.000GB
local             → 0.000GB
```

## Liste quais coleções você possui nesse database (passo 3)

```
VM05(mongod-3.6.3) be-mean-pokemons> show collections;
VM05(mongod-3.6.3) be-mean-pokemons> 
```

## Insira pelo menos 5 pokemons **a sua escolha** utilizando o mesmo padrão de campos utilizado: name, description, type, attack, defense e height (passo 4)

```
VM05(mongod-3.6.3) be-mean-pokemons> var pokemons = [{name:'Suissamon',description:'Pokemon Hacker',type:'hacker',attack:'8001',defense:'8000',height:'1.69'},{name:'Dilmamon',description:'Pokemon presidANTA',type:'besta',attack:'1',defense:'1',height:'1,60'},{name:'Cunhamon',description:'Filho da puta',type:'beta',attack:'9990',defense:'9999',height:'1.80'},{name:'Calheirosmon',description:'Irmão do filho da PUTA',type:'besta',attack:'8500',defense:'9999',height:'1.79'},{name:'FeliciANUS',description:'Pastor baitola',type:'besta',attack:'666',defense:'666',height:'1.70'}];
VM05(mongod-3.6.3) be-mean-pokemons> 

VM05(mongod-3.6.3) be-mean-pokemons> pokemons;
[
  {
    "name": "Suissamon",
    "description": "Pokemon Hacker",
    "type": "hacker",
    "attack": "8001",
    "defense": "8000",
    "height": "1.69"
  },
  {
    "name": "Dilmamon",
    "description": "Pokemon presidANTA",
    "type": "besta",
    "attack": "1",
    "defense": "1",
    "height": "1,60"
  },
  {
    "name": "Cunhamon",
    "description": "Filho da puta",
    "type": "beta",
    "attack": "9990",
    "defense": "9999",
    "height": "1.80"
  },
  {
    "name": "Calheirosmon",
    "description": "Irmão do filho da PUTA",
    "type": "besta",
    "attack": "8500",
    "defense": "9999",
    "height": "1.79"
  },
  {
    "name": "FeliciANUS",
    "description": "Pastor baitola",
    "type": "besta",
    "attack": "666",
    "defense": "666",
    "height": "1.70"
  }
]
VM05(mongod-3.6.3) be-mean-pokemons> 
VM05(mongod-3.6.3) be-mean-pokemons> db.pokemons.insert(pokemons);
Inserted 1 record(s) in 239ms
BulkWriteResult({
  "writeErrors": [ ],
  "writeConcernErrors": [ ],
  "nInserted": 5,
  "nUpserted": 0,
  "nMatched": 0,
  "nModified": 0,
  "nRemoved": 0,
  "upserted": [ ]
})
VM05(mongod-3.6.3) be-mean-pokemons> 
```
## Liste os pokemons existentes na sua coleção (passo 5)

```
VM05(mongod-3.6.3) be-mean-pokemons> db.pokemons.find();
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af32"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": "8001",
  "defense": "8000",
  "height": "1.69"
}
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af33"),
  "name": "Dilmamon",
  "description": "Pokemon presidANTA",
  "type": "besta",
  "attack": "1",
  "defense": "1",
  "height": "1,60"
}
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af34"),
  "name": "Cunhamon",
  "description": "Filho da puta",
  "type": "beta",
  "attack": "9990",
  "defense": "9999",
  "height": "1.80"
}
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af35"),
  "name": "Calheirosmon",
  "description": "Irmão do filho da PUTA",
  "type": "besta",
  "attack": "8500",
  "defense": "9999",
  "height": "1.79"
}
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af36"),
  "name": "FeliciANUS",
  "description": "Pastor baitola",
  "type": "besta",
  "attack": "666",
  "defense": "666",
  "height": "1.70"
}
Fetched 5 record(s) in 40ms
VM05(mongod-3.6.3) be-mean-pokemons> 
```

## Busque um pokemon a sua escolha, que acabou de ser inserido e armazene-o em uma variável chamada 'poke' (passo 6)

```
VM05(mongod-3.6.3) be-mean-pokemons> var query = {"name": "Suissamon"};
VM05(mongod-3.6.3) be-mean-pokemons> 
VM05(mongod-3.6.3) be-mean-pokemons> db.pokemons.find(query);
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af32"),
  "name": "Suissamon",
  "description": "Pokemon Hacker",
  "type": "hacker",
  "attack": "8001",
  "defense": "8000",
  "height": "1.69"
}
Fetched 1 record(s) in 10ms
VM05(mongod-3.6.3) be-mean-pokemons> 
```

## Modifique sua 'description' e salve-o (passo 7)

```
VM05(mongod-3.6.3) be-mean-pokemons> poke.description;
Pokemon Hacker
VM05(mongod-3.6.3) be-mean-pokemons> poke.description = "Pokemon Hacker/Professor";
Pokemon Hacker/Professor
VM05(mongod-3.6.3) be-mean-pokemons> db.pokemons.save(poke);
Updated 1 existing record(s) in 29ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})
VM05(mongod-3.6.3) be-mean-pokemons> 
VM05(mongod-3.6.3) be-mean-pokemons> db.pokemons.findOne(poke);
{
  "_id": ObjectId("5bc7fe7ac8c44afb1f07af32"),
  "name": "Suissamon",
  "description": "Pokemon Hacker/Professor",
  "type": "hacker",
  "attack": "8001",
  "defense": "8000",
  "height": "1.69"
}
VM05(mongod-3.6.3) be-mean-pokemons> 
```
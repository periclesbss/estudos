# MongoDB - Aula 01 - Exercício
autor: Péricles B S Santos

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file /home/pericles/Documentos/MongoDb-ebook-master/src/data/restaurantes.json
2018-10-11T22:55:39.726-0300	connected to: 127.0.0.1
2018-10-11T22:55:39.733-0300	dropping: be-mean.restaurantes
2018-10-11T22:55:42.616-0300	[##################......] be-mean.restaurantes	8.64MB/11.3MB (76.1%)
2018-10-11T22:55:43.282-0300	[########################] be-mean.restaurantes	11.3MB/11.3MB (100.0%)
2018-10-11T22:55:43.282-0300	imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359
```
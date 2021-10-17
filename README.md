# NodeJS In-Memory Database For JSON Objects

__This package is the alpha version of an in-memory DB for an array of JSON objects__

## How to Install

npm i --save memdb-json

## Usage

*This package is still in alpha stage. Before be aware before using in production environment.*

### Initialization

```javascript
const memdb = require('memdb-json');
const MemDB = new memdb(pathToFile); //path to optional JSON file 
```
*You can pass an optional JSON file path to the function for persistant data storage.*

### Insert an object to the DB
````javascript
MemDB.insert({id: 1, Name: "Halil", Surname:"Kutluturk",Age:45,City:"Berlin",Country:"Germany"});
````
### Select object(s) from the DB
````javascript
MemDB.select({where: {City:"Berlin"}});
MemDB.select({where: {Age:45}});
````
*You can query the DB with "where" keyword. Current version only expects one search keyword.
Returns an array of JSON Objects*
### Update an Object in the DB
````javascript
MemDB.update({where: {id: 1}, set: {Born: "New York", Surname: "John", Born: "1998-01-01"}});
````
*Returns a JSON array with updated Objects*
### Delete object(s) from the DB
````javascript
MemDB.delete({where: {id: 1}})
````
### Empty (truncate) the DB
````javascript
MemDB.truncate();
````
### Save the Objects in the DB to a JSON file (persistant data storage)
```javascript
MemDB.save(pathToFile);
```

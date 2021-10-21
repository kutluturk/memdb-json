# In-Memory Database For JSON Objects that can be queried like SQL

__This package is intended to be used as a drop-in small footprint Object database solution for Node.JS.__

## How to Install

npm install --save memdb-json

## Usage

*This package is still in alpha stage. Please be aware before using in production environment.*

### Initialization

```javascript
const memdb = require('memdb-json');
const MemDB = new memdb(pathToFile); //path to optional JSON file 
```

*You can pass an optional JSON file path to the function for persistant data storage.*

### Insert an object to the DB

````javascript
MemDB.insert({id: 1, Name: "Halil", Surname: "Kutluturk", Age: 45, City: "Berlin", Country: "Germany"});
````

*Returns a UUID of the object inserted to the DB*

### Select object(s) from the DB

````javascript
MemDB.select({where: {City: "Berlin"}});
MemDB.select({where: {Surname: "Smith", Age: 45}}); // You can add multiple keywords
MemDB.select(); //Returns all objects
````

*You can query the DB with "where" keyword.*\
*Returns an array of JSON Objects*

### Update an Object in the DB

````javascript
MemDB.update({where: {id: 1}, set: {Born: "New York", Surname: "John", Born: "1998-01-01"}});
MemDB.update({where: {Name: "John", Surname: "Smith", Nationality: "USA"}, set: {Born: "New York", Active: true}});

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

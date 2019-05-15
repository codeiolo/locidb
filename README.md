[![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

# lociDB

## Intro
Small and simple noSQL-like database module for NodeJS applications.

This module lets you store an array of objects into simple plain text files as a JSON string.
You dont need to stringify your objects first, lociDB does that for you (see usage below).

This noSQL-like database is perfect for your small NodeJS and Electron applications where you 
maby want to store some kind of user settings, todo-list etc for example.

See our [change log](https://github.com/luxwarp/locidb/wiki/Change-log) in the wiki.

If you planing on storing >100MB of data this module is not for you.

## Install
`npm install --save locidb`

## Usage

```javascript
const LociDB = require('./index')                       // Import the module.
const db = new LociDB()                                 // Create an instance of lociDB.

let user = {                                            // This is three example objects
  name: 'Mikael',
  age: 27,
  city: 'Bohus',
  country: 'Sweden'
}

let user2 = {
  name: 'Kalle',
  age: 27,
  city: 'Nol',
  country: 'Norway'
}

let settings = {
  fontSize: 13,
  color: '#000',
  active: false
}

console.log(db.listTables())                            // First list tables to se if it exists any already.

db.set('users', user)
db.set('settings', settings)                            // This will overwrite any data in the table and insert the value instead.

db.insert('users', user2)                               // Insert the object to the table at the end.

console.log(db.countRows('users'))                      // Count how many rows there is in a table.

console.log(db.get('users'))                            // Get all rows in the table as an array of objects and print it.
console.log(db.get('settings'))

console.log(db.getRows('users', 'name', 'Mikael'))      // Get all rows in a table matching a key and a value as an array of objects.

console.log(db.dropRows('users', 'name', 'Mikael'))     // Drop/delete specific rows in a table. Returns a number of total rows deleted.
db.dropTable('settings')                                // Drop/delete a specific table. Returns true if a delete was made of false if not.
db.dropAll();                                           // Drop/deletes all tables. Use only if you know what you doing.
```

## Testing
If you want to try some functions before using this module 
in your applications you can use the `test.js` file located in the
root folder of the module and then run the file in your terminal with the command
`node ./test.js`

## License
ISC - © Copyright [Mikael Carlsson](https://luxwarp.info)

## Note
Feel free to contribute the way you want.
# TCP 27017: MongoDB

> MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas. MongoDB is developed by MongoDB Inc. and licensed under the Server Side Public License.
>
>  -- <cite>[Wikipedia](https://en.wikipedia.org/wiki/MongoDB)</cite>

## Terms

* Collections are like tables
* Documents are like rows
* Fields are like columns

## Common operators

* $eq
* $ne
* $gt
* $where
* $exists
* $regex

## Basic commands

Show databases
```bash
show databases
```

Select database
```bash
use <database>
```

Create database
```bash
use <database>
```

Create collection 
```bash
db.createCollection("<collection>")
```

Show collections
```bash
db.getCollectionNames()
```

Create document
```bash
db.<collection>.insert(<json>)
```

Query collection
```bash
db.<collection>.find()
```

Update document
```bash
db.<collection>.update(<where-json>, { $set: <update-json> })
```

Delete document
```bash
db.<collection>.remove(<where-json>)
```

## NoSQL injection

### Via JSON

Use e.g. `{ "$ne": "whatever" }` as password to bypass login logic.

### Via requests

Inject `$ne` in GET param `?username[$ne]=name` to invert the logic.

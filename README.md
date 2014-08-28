mysql-mirror-database
=====================

Node Module - Mirrors a remote MySQL database using only SELECT.  This solves a very specific problem, see the intent and requirements sections below.

Note, if using this module you must run your app using the harmony flag, e.g.:
```
node --harmony app.js
```

### Intent
Let's say you have access to a remote database but only have one privilege: SELECT.  Perhaps you want a local copy of this database for your app to work with, or maybe you want to be able to create views or stored procedures to work with this data.  This app will create a local copy of the remote database, given a few strict requirements.

### Requirements
* The remote database is INSERT only.  Records are not updated
* Each table has an auto-increment column with the same name

### Example App

```
"use strict";

// This is the database we want to mirror
var remotedb_json = {
    host: 'some_ip',
    port: 'some_port',
    user: 'some_user',
    password: 'some_password',
    database: 'some_database'
};

// This is the destination database
var destinationdb_json = {
    host: 'another_ip',
    port: 'another_port',
    user: 'another_user',
    password: 'another_password',
    database: 'another_database'
};

// Note, 'event_number' below is the common autoincrement field
new require('mysql-mirror-database')(remotedb_json, destinationdb_json, 'event_number');
```
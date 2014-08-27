mysql-mirror-database
=====================

Node Module - Mirrors a remote MySQL database using only SELECT

Note, if using this module you must run your app using the harmony flag, e.g.:
```
node --harmony app.js
```

###Example App

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

new require('mysql-mirror-database')(remotedb_json, destinationdb_json);
```
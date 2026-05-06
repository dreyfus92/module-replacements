---
description: Modern alternatives to the sqlite3 package for working with SQLite in Node.js
---

# Replacements for `sqlite3`

## `node:sqlite` (native, since Node.js 22.13.0)

Node.js ships a built-in SQLite module, [`node:sqlite`](https://nodejs.org/api/sqlite.html), which is the preferred option when you can target a recent Node runtime.

Example:

```ts
import sqlite3 from 'sqlite3' // [!code --]
import { DatabaseSync } from 'node:sqlite' // [!code ++]

const db = new sqlite3.Database('app.db') // [!code --]
const db = new DatabaseSync('app.db') // [!code ++]

db.all('SELECT * FROM users', (err, rows) => {}) // [!code --]
const rows = db.prepare('SELECT * FROM users').all() // [!code ++]
```

## `better-sqlite3`

[`better-sqlite3`](https://github.com/WiseLibs/better-sqlite3) is a popular and actively maintained SQLite library for Node.js.

Example:

```ts
import sqlite3 from 'sqlite3' // [!code --]
import Database from 'better-sqlite3' // [!code ++]

const db = new sqlite3.Database('app.db') // [!code --]
const db = new Database('app.db') // [!code ++]

db.all('SELECT * FROM users', (err, rows) => {}) // [!code --]
const rows = db.prepare('SELECT * FROM users').all() // [!code ++]
```

## Notes Backend

Notes allows users to add, edit, delete, and save user notes. Each user only has access to their individual notes and not all the notes in the database.

## Tech

Node.js
PostgreS
Knex
Express
Heroku
JWT Tokens

## Data Models

All data models are built using migrations created with SQL query bulder Knex.js. The migrations are structured for a Postgres database.

### Users Table

The users table is used to store the username and password only.

```

Users Table Data Model

        users.increments();
        users
            .string('username', 128)
            .notNullable()
            .unique();
        users
            .string('password')
            .notNullable();

```

The notes table is used to store a title, textbody, tags, and a foreign key tied to the user's table/id.

```
Notes Table Data Model

        tbl.increments();

        tbl
            .string('title', 255)
            .notNullable();
        tbl
            .string('textBody')
            .notNullable();
        tbl
            .string('tags');
        tbl
            .integer('users_id')
            .unsigned()
            .references('id')
            .inTable('users')
            .notNullable();

```

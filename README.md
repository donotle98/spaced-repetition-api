# Spaced repetition API!

<p>Server uses a linked list data structure to keep track of the words the user needs to learn</p>
<h2>API documentation</h2>
<span>POST '/api/auth'</span>
<p>Posting a login with a username and password, this endpoint will make sure they match and will create a json web token</p>
<span>GET '/api/language/'</span>
<p>Endpoint will get the words for the user</p>
<span>GET '/api/language/head'</span>
<p>Endpoint will get the word the user is learning next</p>
<span>GET '/api/language/guess'</span>
<p>Endpoint will get the user's guess and compare it to the translation in the database</p>
<span>POST '/api/user/</span>
<p>Endpoint will post a new user when signing up, only needing a Username, Name, and Password</p>

## Local dev setup

If using user `dunder-mifflin`:

```bash
mv example.env .env
createdb -U dunder-mifflin spaced-repetition
createdb -U dunder-mifflin spaced-repetition-test
```

If your `dunder-mifflin` user has a password be sure to set it in `.env` for all appropriate fields. Or if using a different user, update appropriately.

```bash
npm install
npm run migrate
env MIGRATION_DB_NAME=spaced-repetition-test npm run migrate
```

And `npm test` should work at this point

## Configuring Postgres

For tests involving time to run properly, configure your Postgres database to run in the UTC timezone.

1. Locate the `postgresql.conf` file for your Postgres installation.
    1. E.g. for an OS X, Homebrew install: `/usr/local/var/postgres/postgresql.conf`
    2. E.g. on Windows, _maybe_: `C:\Program Files\PostgreSQL\11.2\data\postgresql.conf`
    3. E.g on Ubuntu 18.04 probably: '/etc/postgresql/10/main/postgresql.conf'
2. Find the `timezone` line and set it to `UTC`:

```conf
# - Locale and Formatting -

datestyle = 'iso, mdy'
#intervalstyle = 'postgres'
timezone = 'UTC'
#timezone_abbreviations = 'Default'     # Select the set of available time zone
```

## Scripts

Start the application `npm start`

Start nodemon for the application `npm run dev`

Run the tests mode `npm test`

Run the migrations up `npm run migrate`

Run the migrations down `npm run migrate -- 0`

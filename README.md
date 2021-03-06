# run-rs

Zero-config MongoDB runner. Starts a replica set with no non-Node dependencies, not even MongoDB.

## Usage

To install:

```
npm install run-rs -g
```

With run-rs, starting a 3 node [replica set](https://docs.mongodb.com/manual/tutorial/deploy-replica-set/) running MongoDB 3.6 is a one-liner.

```
run-rs
```

To use a different version, use the `-v` flag. For example, this will start a 3 node replica set using MongoDB 4.0.0.

```
run-rs -v 4.0.0
```

## Clearing the Database

Run-rs clears the database every time it starts by default. To override this behavior, use the `--keep` (`-k`) flag.

```
run-rs --keep
```

## OS Support

Run-rs supports Linux, OSX, and Windows 10 (via [git bash](https://git-scm.com/downloads) or powershell).

## Shell Option

Use the `--shell` flag to start a MongoDB shell connected to your replica
set once the replica set is running.

```
$ run-rs --shell
Purging database...
Running '/home/node/lib/node_modules/run-rs/3.6.5/mongod'
Starting replica set...
Started replica set on "mongodb://localhost:27017,localhost:27018,localhost:27019"
Connecting shell /home/node/lib/node_modules/run-rs/3.6.5/mongo
rs:PRIMARY>
```

## Notes on Connecting

Use `replicaSet=rs` in your connection string. 

## Reusing a Pre-installed MongoDB Version

By default, run-rs will download whatever version of MongoDB you've specified. If you already have MongoDB installed, you can use the `--mongod` option:

```
run-rs --mongod
```

The above command will just run whatever `mongod` is on your PATH. If you want to run a specific `mongod` server, you can do this:

```
run-rs --mongod /home/user/path/to/mongod
```

## Specify the data directory

By default, run-rs will store data files in a directory named 'data'. To specify a dbPath for run-rs to use as a data directory, use the `--dbpath` option.

```
run-rs --dbPath /path/to/data/directory
```

## Running in Production

Do **not** use run-rs for running your production database. Run-rs is designed
for local development and testing, and is not intended for production use.
If you want to run MongoDB in production and don't want to manage a replica
set yourself, use [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).

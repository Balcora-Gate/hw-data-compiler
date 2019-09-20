# hw-data-compiler

Real simple tool for compiling extracted mod data into JSON format. Point the script to the root of the mod, specify entity types to compile, watch it go.

<p align="center"><img src="https://i.imgur.com/uMvwk6r.png" alt="BALCORA" /></p>

---

## Usage

1. Clone this repo somewhere (`git clone https://github.com/HW-PlayersPatch/hw-data-compiler.git`)
    1. If you want to use this within your own project, `npm install hw-data-compiler`
2. Navigate into the cloned repo (probably with `cd hw-data-compiler`) and run `npm install`
3. `npm run compile` is the command to run the script, **it can take two flags:**
    1. `-w`: 'Write to file', writes the compiled data into a file called `dump.json`
    2. `-db`: 'Write to database', writes the compiled data into an Atlas database according to variables in your `.env` file (see below).
4. Follow the prompts:
    1. Enter the root of the mod you want to compile (the directory containing the `keeper.txt` file)
    2. Indicate which data categories you're interested in (comma seperated), valid arguments are `ship`, `weapon`, `subsystem`
5. Data will be parsed and compiled, and written to the flagged destinations.

### .env

The `-db` flag expects certain variables to be present in a file called `.env`. Create this file via `touch` or however you like, make sure it's in the same directory as the mains script. Inside `.env`, you need to supply four variables:
- `CLUSTER_USER_NAME`, the name of the cluster user
- `CUSTER_USER_PASS`, the password of the cluster user
- `CLUSTER_STR`, the connection string of the cluster
- `CLUSTER_DB_NAME` the database to use

For example:
```
CLUSTER_STR=balcora-0jmga.mongodb.net/test?retryWrites=true&w=majority
CLUSTER_USER_NAME=Fear
CLUSTER_USER_PASS=my_password
CLUSTER_DB_NAME=game_data_playerspatch_11
```
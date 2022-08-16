# Singer.io Pipeline 


Pipeline to take data from MySQL and dump to PostgresSQL

Virtual Environments:

I recommend you create separate env's for tap and target.
Please update the below code to use respective venvs.


Steps:
1) Create venv for tap and target
   a) install mysql tap using `pip install tap-mysql` on tap venv
   b) install postgres target using `pip install singer-target-postgres` on target venv
  
2) Update config for tap under `mysql_config.json`

3) Update config for target under `postgres_config.json`

4) Run in discovery mode
   `{tap venv_name/bin/}tap-mysql --config mysql_config.json --discover > catalog.json`
   
5) Select the one of the stream from the `catalog.json` and create new file with it called `properties.json`. For this example I have used employee table from mysql db. You can find dump in file named `SQL-dump.sql` .

6) Update the `properties.json` and add `'selected': true` and `replication-method` to `properties.json` according to your need. For this I have already updated `properties.json`

7) run command
   `{tap venv_name/bin/}tap-mysql -c mysql_config.json --properties properties.json | {target venv_name/bin/}target-postgres -c postgres_config.json >> state.json   
   `

### For more taps and targets: https://github.com/singer-io


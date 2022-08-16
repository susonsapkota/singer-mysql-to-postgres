# Singer.io Pipeline 


Pipeline to take data from MySQL and dump to PostgresSQL

Virtual Environments:

For now using same env for both tap and target,
I recommend you create separate env's for tap and target. (This is not recommended at all)
Please update the below code to use respective venvs.


Steps:
1) Switch to environment
2) Run in discovery mode
   `tap-mysql --config mysql_config.json --discover > catalog.json`
3) Select the one of the stream from the catalog.json and create new file with it called properties.json
4) Update the properties.json and add "'selected': true" and "replication-method" to properties.json
5) run command
   `tap-mysql -c mysql_config.json --properties properties.json | target-postgres -c postgres_config.json >> state.json   
   `



### For more taps and targets: https://github.com/singer-io


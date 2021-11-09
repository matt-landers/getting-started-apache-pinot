# Batch Load a Table

## Create the Schema

From the `/bin` directory, run the following command:

```
./pinot-admin.sh AddSchema -schemaFile ../examples/batch/baseballStats/baseballStats_schema.json -exec
```

This will create a Pinot Schema that we'll use to create a table.

## Create the Table

After creating the Schema, run the following command from the `/bin` directory to create the table:

```
./pinot-admin.sh AddTable -tableConfigFile ../examples/batch/baseballStats/baseballStats_offline_table_config.json -exec
```

Now, we'll load the data into the table.

## Load the Data

In order to load data into the table, we need to run an IngestionJob.

Open the job specification:

```
vim ../examples/batch/baseballStats/​​ingestionJobSpec.yaml
```

Change the input and output directories to be absolute:

```
inputDirURI: 'app/pinot/examples/batch/baseballStats/rawdata'
outputDirURI: 'app/pinot/examples/batch/baseballStats/segments'
```

Run the job file:

```
./pinot-admin.sh LaunchDataIngestionJob -jobSpecFile ../examples/batch/baseballStats/​​ingestionJobSpec.yaml
```

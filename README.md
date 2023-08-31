Convert parquet repro
===

### The setup

The file iris.csv exists in a local postgres database. 

I exported it to parquet using the command

```sh
pg2parquet_0.1-beta.6 export --host localhost --port 5432 --dbname my_db --output-file iris.parquet -t $iris
```

I'm trying to convert it to arrow using [`parquet2arrow`](https://github.com/alexkreidler/parquet2arrow).

Using this command

```sh
parquet2arrow --input iris.parquet --output iris.arrow
```

I get the following error:

```txt
Error: Failed to get Arrow schema from Parquet

Caused by:
    Arrow: Unable to convert parquet BYTE_ARRAY logical type Some(DECIMAL(DecimalType { scale: 18, precision: 38 })) or converted type DECIMAL
```

I'm wondering if the parquet file needs to be written with an additional schema to prepare it for the arrow format. 

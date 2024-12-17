# Secret Duck

Convert a Keepass database into [DuckDB secrets](https://duckdb.org/docs/configuration/secrets_manager.html) that may
be loaded into DuckDB using its secret manager feature.

# Installation

```bash
pip install secret-duck
```

# Usage

The first required argument is the path of the Keepass file. You must also provide the [type of secrets](https://duckdb.org/docs/configuration/secrets_manager.html#types-of-secrets) you want to generate e.g. S3, GCS, etc.

```bash
secret-duck --help
```
```
usage: secret-duck [-h] [--log_level {DEBUG,INFO,WARNING,ERROR,CRITICAL}] [--password PASSWORD] --type TYPE [--persistent] [--replace] [--if_not_exists] [--keys KEYS] keepass_file

positional arguments:
  keepass_file          Keepass database file

options:
  -h, --help            show this help message and exit
  --log_level {DEBUG,INFO,WARNING,ERROR,CRITICAL}
  --password PASSWORD
  --type TYPE, -t TYPE  DuckDB secret type e.g. S3
  --persistent
  --replace
  --if_not_exists
  --keys KEYS, -k KEYS  JSON dictionary of key-value pairs e.g. {"region":"eu-west-2"}
```

## Examples

To create AWS S3 secrets

```bash
secret-duck my_secrets.kdbx --type S3 --keys {\"endpoint\": \"s3.amazonaws.com\"}
```

To create AWS S3 secrets and save the results to an SQL file

```bash
secret-duck my_secrets.kdbx --type S3 --keys {\"region\": \"eu-west-2\", \"endpoint\": \"s3.amazonaws.com\"} > secrets.sql
```

# Secret Duck

Convert a Keepass database into DuckDB secrets.

# Installation

```bash
pip install secret-duck
```

# Usage

```bash
secret-duck --help
```

To create AWS S3 secrets and save the results to an SQL file.

```bash
secret-duck my_secrets.kdbx --type S3 --keys {\"region\": \"eu-west-2\", \"endpoint\": \"s3.amazonaws.com\"} > secrets.sql
```

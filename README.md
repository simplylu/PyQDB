## Description

API wrapper following the basic API requirements of QuestDB described [here](https://questdb.io/docs/reference/api/rest/).

## Usage

Install requirements:

```sh
pip3 install -r requirements.txt
```

Import

```python
from PyQDB import QuestDB

qdb = QuestDB()
```

## Methods

### /imp - Import

*`/imp` streams tabular text data directly into a table. It supports CSV, TAB and pipe (`|`) delimited inputs with optional headers. There are no restrictions on data size. Data types and structures are detected automatically, without additional configuration. In some cases, additional configuration can be provided to improve the automatic detection as described in [user-defined schema](https://questdb.io/docs/reference/api/rest/#user-defined-schema).*

```py
res = qdb.imp(filename="test.csv", name="PyQDB")
```

> See `qdb_api.py` or [API reference](https://questdb.io/docs/reference/api/rest/#imp---import-data) for all possible parameters.

### /exec - Execute queries

*`/exec` compiles and executes the SQL query supplied as a parameter and returns a JSON response.*

```py
res = qdb.exec(query="SELECT * FROM PyQDB")
```

**SQL queries will be verified via `sqlvalidator==0.0.17` there might be issues with QuestDB SQL Syntax.**

> See `qdb_api.py` or [API reference](https://questdb.io/docs/reference/api/rest/#exec---execute-queries) for all possible parameters.

### /exp - Export data

*This endpoint allows you to pass url-encoded queries but the request body is returned in a tabular form to be saved and reused as opposed to JSON.*

```py
res = qdb.exp(query="SELECT * FROM PyQDB")
```

> See `qdb_api.py` or [API reference](https://questdb.io/docs/reference/api/rest/#exp---export-data) for all possible parameters.
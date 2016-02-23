# Oracle Database drivers for Go

There are 2 main drivers for Oracle Database in Go:

1. [mattn/go-oci8](https://github.com/mattn/go-oci8)
2. [rana/ora](https://github.com/rana/ora)

I prefer `rana/ora` because it supports calling of stored procedures.

### rana/ora

To install `rana/ora` driver use:

    CGO_LDFLAGS=-L$ORACLE_HOME CGO_CFLAGS=-I$ORACLE_HOME/sdk/include go get gopkg.in/rana/ora.v3

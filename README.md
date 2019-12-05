# CSV

Docker container to run CSV manipulation utitilies (csvtool, csvkit...).

## Example

Assuming that you have a CSV file `foo.csv` and that you want to extract the column named `bar`:

### Mac/Linux

```
$ cat foo.csv | docker run --rm -i --net=none thomasleplus/csv csvsql --table foo --query "select bar from foo"
```

### Windows

```
$ type foo.csv | docker run --rm -i --net=none thomasleplus/csv csvsql --table foo --query "select bar from foo"
```

## Help

To know more command line options of one of the csvtk command:

```
$ docker run --rm --net=none thomasleplus/csv csvsql -h
```

# CSV

Docker container to run CSV manipulation utitilies (csvtool, csvkit...).

## Example not using the filesystem

Let's say that you have a CSV file `foo.csv` and that you want to extract the column named `bar`:

### Mac/Linux

```
cat foo.csv | docker run --rm -i --net=none thomasleplus/csv csvsql --table foo --query "select bar from foo"
```

### Windows

```
type foo.csv | docker run --rm -i --net=none thomasleplus/csv csvsql --table foo --query "select bar from foo"
```

## Example using the filesystem

Same thing, assuming that you have a CSV file `foo.csv` and that you want to extract the column named `bar`:

### Mac/Linux

```
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/csv csvsql --query "select bar from foo" /tmp/foo.csv
```

### Windows

In `cmd`:

```
docker run --rm -t --net=none -v "%cd%:/tmp" thomasleplus/csv csvsql --query "select bar from foo" /tmp/foo.csv
```

In PowerShell:

```
docker run --rm -t --net=none -v "${PWD}:/tmp" thomasleplus/csv csvsql --query "select bar from foo" /tmp/foo.csv
```

## Help

To know more command line options of one of the csvtk command:

```
docker run --rm --net=none thomasleplus/csv csvsql -h
```

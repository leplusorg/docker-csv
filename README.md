# CSV

Docker container to run CSV manipulation utitilies (csvtool, csvkit...).

## Example

Assuming that you have a CSV file `foo.csv` and that you want to extract the column named `bar`:

### Mac/Linux

```
$ docker run --rm -it --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" thomasleplus/csv csvsql --query "select f.bar from foo as f" /tmp/foo.csv
```

### Windows

In `cmd`:

```
$ docker run --rm -it --net=none -v "%cd%:/tmp" thomasleplus/csv csvsql --query "select f.bar from foo as f" /tmp/foo.csv
```

In PowerShell:

```
$ docker run --rm -it --net=none -v "${PWD}:/tmp" thomasleplus/csv csvsql --query "select f.bar from foo as f" /tmp/foo.csv
```

## Help

To know more command line options of one of the csvtk command:

```
$ docker run --rm -it --net=none thomasleplus/csv csvsql -h
```

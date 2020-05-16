# CSV

Docker container to run CSV manipulation utitilies (csvtool, csvkit...).

![Docker Stars](https://img.shields.io/docker/stars/thomasleplus/csv.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/thomasleplus/csv.svg)
![Docker Automated](https://img.shields.io/docker/automated/thomasleplus/csv.svg)
![Docker Build](https://img.shields.io/docker/build/thomasleplus/csv.svg)

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

## Request new tool

Please use [this link](https://github.com/thomasleplus/docker-csv/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.

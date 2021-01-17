# CSV

Docker container to run CSV manipulation utitilies (csvkit...).

[![Docker Build](https://github.com/thomasleplus/docker-csv/workflows/Docker/badge.svg)](https://github.com/thomasleplus/docker-csv/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/thomasleplus/csv)](https://hub.docker.com/r/thomasleplus/csv)
[![Docker Pulls](https://img.shields.io/docker/pulls/thomasleplus/csv)](https://hub.docker.com/r/thomasleplus/csv)
[![Docker Automated](https://img.shields.io/docker/cloud/automated/thomasleplus/csv)](https://hub.docker.com/r/thomasleplus/csv)
[![Docker Build](https://img.shields.io/docker/cloud/build/thomasleplus/csv)](https://hub.docker.com/r/thomasleplus/csv)
[![Docker Version](https://img.shields.io/docker/v/thomasleplus/csv?sort=semver)](https://hub.docker.com/r/thomasleplus/csv)

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

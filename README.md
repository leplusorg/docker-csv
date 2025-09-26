# CSV

Multi-platform Docker container with utilities to process CSV files (`csvkit`, `csvcut`, `csvgrep`, `csvsql`, `csvjson`, `csvq`...).

[![Dockerfile](https://img.shields.io/badge/GitHub-Dockerfile-blue)](csv/Dockerfile)
[![Docker Build](https://github.com/leplusorg/docker-csv/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-csv/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/csv)](https://hub.docker.com/r/leplusorg/csv)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/csv)](https://hub.docker.com/r/leplusorg/csv)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/csv?sort=semver)](https://hub.docker.com/r/leplusorg/csv)
[![CII Best Practices](https://bestpractices.coreinfrastructure.org/projects/10076/badge)](https://bestpractices.coreinfrastructure.org/projects/10076)
[![OpenSSF Scorecard](https://api.securityscorecards.dev/projects/github.com/leplusorg/docker-csv/badge)](https://securityscorecards.dev/viewer/?uri=github.com/leplusorg/docker-csv)

## Example not using the filesystem

Let's say that you have a CSV file `foo.csv` and that you want to extract the column named `bar`:

**Mac/Linux**

```bash
cat foo.csv | docker run --rm -i --net=none leplusorg/csv csvsql --table foo --query "select bar from foo"
```

**Windows**

```batch
type foo.csv | docker run --rm -i --net=none leplusorg/csv csvsql --table foo --query "select bar from foo"
```

## Example using the filesystem

Same thing, assuming that you have a CSV file `foo.csv` and that you want to extract the column named `bar`:

**Mac/Linux**

```bash
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" leplusorg/csv csvsql --query "select bar from foo" /tmp/foo.csv
```

**Windows**

In `cmd`:

```batch
docker run --rm -t --net=none -v "%cd%:/tmp" leplusorg/csv csvsql --query "select bar from foo" /tmp/foo.csv
```

In PowerShell:

```pwsh
docker run --rm -t --net=none -v "${PWD}:/tmp" leplusorg/csv csvsql --query "select bar from foo" /tmp/foo.csv
```

## Help

To know more command-line options of one of the csvtk command:

```bash
docker run --rm --net=none leplusorg/csv csvsql -h
```

## Software Bill of Materials (SBOM)

To get the SBOM for the latest image (in SPDX JSON format), use the
following command:

```bash
docker buildx imagetools inspect leplusorg/csv --format '{{ json (index .SBOM "linux/amd64").SPDX }}'
```

Replace `linux/amd64` by the desired platform (`linux/amd64`, `linux/arm64` etc.).

### Sigstore

[Sigstore](https://docs.sigstore.dev) is trying to improve supply
chain security by allowing you to verify the origin of an
artifcat. You can verify that the image that you use was actually
produced by this repository. This means that if you verify the
signature of the Docker image, you can trust the integrity of the
whole supply chain from code source, to CI/CD build, to distribution
on Maven Central or whever you got the image from.

You can use the following command to verify the latest image using its
sigstore signature attestation:

```bash
cosign verify leplusorg/csv --certificate-identity-regexp 'https://github\.com/leplusorg/docker-csv/\.github/workflows/.+' --certificate-oidc-issuer 'https://token.actions.githubusercontent.com'
```

The output should look something like this:

```text
Verification for index.docker.io/leplusorg/xml:main --
The following checks were performed on each of these signatures:
  - The cosign claims were validated
  - Existence of the claims in the transparency log was verified offline
  - The code-signing certificate was verified using trusted certificate authority certificates

[{"critical":...
```

For instructions on how to install `cosign`, please read this [documentation](https://docs.sigstore.dev/cosign/system_config/installation/).

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-csv/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.

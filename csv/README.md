# csv image

Build context for the `leplusorg/csv` container image. See the
[root readme](../README.md) for what the image does and how to run it.

## Files

- `Dockerfile` — the image definition. System packages come from the base
  distribution's package manager and are pinned to exact versions here.
- `docker-compose.test.yml` — the smoke test run in CI against the built image:
  the `sut` service checks that the container runs as the non-root user (UID
  1000) and that each bundled tool starts.
- `requirements.txt` — the Python tools installed in the image, with their
  pinned versions. The `Dockerfile` installs each one globally with `pipx`, in
  its own virtual environment.

## Manifests

The manifest (`requirements.txt`) exposes the pinned versions of some of the
packages and tools included in the image in a machine-readable format. It can be
used to generate an SBOM, and it is kept up to date automatically by Dependabot
(see [`dependabot.yml`](../.github/dependabot.yml)); Renovate would work too.

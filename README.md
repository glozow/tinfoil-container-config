# Tinfoil Containers

Deployment repository for [Tinfoil Containers](https://docs.tinfoil.sh/containers/overview) — Docker containers that run in secure enclaves.

Rather than create separate deployment repos, this repo holds the `tinfoil-config.yml` for **every** Tinfoil service.

## Layout

- **`main`** — base template. Holds changes that apply to every
  service: `cvm-version` bumps, CI workflow updates, shim-template
  changes, repo-wide policy. **Nothing service-specific lands here.**
- **`guard`**, **`gated-inference`**, ... — one branch per service.
  Branch from main when creating a new service.
  Each branch holds the `tinfoil-config.yml`for that service.
  Tags for that service are cut from this
  branch and nowhere else.

## Tag convention

`<service>-vX.Y.Z` — e.g. `guard-v0.0.1`, `gated-inference-v0.1.2`.

- The `<service>-` prefix matches the branch name.
- `vX.Y.Z` is a standard semver for that service's image pin.
- **Only ever tag from the service branch**, never from `main`.


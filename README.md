# github-dwh-vultr

Live desired state for the single-host getcolors GitHub warehouse at [github-dwh.bigconfig.space](https://github-dwh.bigconfig.space).

```sh
./blue build
./blue create --dry-run
./blue create
./blue run
```

The deployment ingests every repository accessible to the GitHub organization token into ClickHouse, builds dbt models, and exposes PocketBase as a whole-workflow control plane. Full logs remain in journald.

`colors.yml` is the only desired-state file. `.colors/`, `.ssh/`, and `.envrc.private` are local, ignored, and sensitive. Deletion is protected by `compute-prevent-destroy: true`.

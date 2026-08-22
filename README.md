# github-dwh-vultr

Live desired state for the single-host getcolors GitHub warehouse at [github-dwh.bigconfig.space](https://github-dwh.bigconfig.space), with Lightdash analytics at [analytics.github-dwh.bigconfig.space](https://analytics.github-dwh.bigconfig.space).

```sh
./blue build
./blue create --dry-run
./blue create
# Start production loads from the PocketBase control plane.
```

The deployment ingests every repository accessible to the GitHub organization token into ClickHouse, builds dbt models, exposes PocketBase as a whole-workflow control plane, and publishes the tested marts through read-only Lightdash dashboards. Full logs remain in journald. Production runs are requested at [github-dwh.bigconfig.space](https://github-dwh.bigconfig.space); the host executes them as transient systemd units. Recovery procedures live in [`getcolors/github-dwh`](https://github.com/getcolors/github-dwh/blob/main/RECOVERY.md).

`colors.yml` is the only desired-state file. `.colors/`, `.ssh/`, and `.envrc.private` are local, ignored, and sensitive. Deletion is protected by `compute-prevent-destroy: true`.

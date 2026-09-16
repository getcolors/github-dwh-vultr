# CLAUDE.md

## Repository

Desired-state deployment of `getcolors/github-dwh` on one Vultr VM. ClickHouse, PocketBase, Caddy, the systemd dispatcher, and Blue/dlt/dbt all run on that host. `colors.yml` is source; `.colors/` is generated. Desired state now targets the shared R2 backend (`github-dwh-vultr/tofu.tfstate`), but until `tofu init -migrate-state` has moved it, `.colors/` still holds the live local OpenTofu state. Never edit or delete it while the deployment exists.

## Commands

```sh
./blue build
./blue create --dry-run
./blue run --dry-run
./blue create
./blue run
```

Secrets live only in ignored `.envrc.private`. Never read it, export `COLORS_PAR_PROFILE`, commit `.colors/` or `.ssh/`, or weaken `compute-prevent-destroy`. Real create/run/delete requires explicit authorization. The root `blue` is a copy of `.agents/skills/package-github-dwh-blue/blue`; synchronize it after every skill update.

## Git

Work on the current branch. Do not commit or push unless explicitly authorized.

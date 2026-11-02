# SharkyPHP release splitter

Release-only repository. Do not commit framework code here.

- `main` holds the splitter workflow and a once-per-day heartbeat file.
- `mirror` is a read-only mirror of the public monorepo.
- Every hour the workflow clones the public monorepo **without any credential**, splits `packages/*` into 22 standalone repositories in this organization, and force-pushes `main` plus every `v*` tag.
- The 22 split repositories are read-only mirrors. Please open issues and pull requests in the monorepo instead.
- The only publishing credential lives in this repository's Actions secrets.

Releases are triggered by tagging the monorepo: `git tag v2.0.0 && git push origin v2.0.0`.

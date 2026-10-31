# go-embedded-julia.github.io

The go-embedded-julia landing page (Hugo), served at <https://go-embedded-julia.github.io/>.
The documentation is at <https://go-embedded-julia.github.io/docs/> (repository
[go-embedded-julia/docs](https://github.com/go-embedded-julia/docs)).

The organization is **in development**. `go-embedded-julia/julia` v0.3.0
(2026-10-28) completes milestones M0 (the oracle harness), M1 (the parser,
identical to `Meta.parseall` on 1191 of 1191 files of julia 1.12.6's tree) and
M2 (lowering, identical to `Meta.lower` on 53 997 of 53 997 forms of that tree);
M3 (the Core runtime) is in progress, and the page says so: v0.9.0 (2026-10-31)
runs `struct` and `abstract type` definitions (with parameters) and methods with `where` clauses in the package `interp` (lowered code over Core), next to Julia's type objects,
subtyping, method specificity and the dispatch of concrete calls. It gives what the
interpreter will be, the milestones M0 to M7, the runtime boundary with its
counts, and the honest scope: an interpreter, which keeps Julia's semantics and
not its native speed. Its statements come from the roadmap's bibliography,
`bib/julia.md` in [go-scikit/roadmap](https://github.com/go-scikit/roadmap)
(on main). There is no playground yet, so there is no playground button.

The layout is the go-* family template: `layouts/index.html` and the shared
design (stylesheet, theme toggle, fork ribbon, icons), imported as the Hugo module
`github.com/go-fleettools/landingkit` pinned in `go.mod`. `[params.brand]`
in `hugo.toml` is read from the logo's gradient:

```sh
go run github.com/go-fleettools/landingkit/cmd/landingkit brand static/img/logo.svg
hugo server
```

| Workflow | What |
| --- | --- |
| `hugo.yml` | builds on pull requests; builds and deploys to Pages on `main` |
| `ci.yml` | the site builds and names every repository; `go mod tidy` keeps the landingkit requirement |
| `links.yml` | every link and image of the built site resolves |

BSD-3-Clause.

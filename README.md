# go-embedded-julia.github.io

The go-embedded-julia landing page (Hugo), served at <https://go-embedded-julia.github.io/>.
The documentation is at <https://go-embedded-julia.github.io/docs/> (repository
[go-embedded-julia/docs](https://github.com/go-embedded-julia/docs)).

The organization is **in development**. `go-embedded-julia/julia` v0.13.0
(2026-11-14) completes milestones M0 (the oracle harness), M1 (the parser,
identical to `Meta.parseall` on 1191 of 1191 files of julia 1.12.6's tree; v0.2.0),
M2 (lowering, identical to `Meta.lower` on 53 997 of 53 997 forms of that tree; v0.3.0)
and M3 (the runtime): the interpreter runs julia
1.12.6's real Base and seven stdlibs (FileWatching, Libdl, Artifacts, SHA,
Sockets, LinearAlgebra, Random), with tasks, an event loop and a virtual file
system in two modes (sandbox and host). The page gives its known limits:
dynamic libraries are the Go-implemented ones (loading a C library is a stated
divergence), the stdlibs are still julia's `.jl` sources (#36), no LAPACK or
level-3 BLAS beyond `gemm` yet (#67), no host-mode file writes yet (#32), and a
slow `@async` comprehension. The current release is v0.19.0: the page names it
(`Kernel.Reset`, `A * x` through go-blas, utf8proc in Go) and the interpreter's
measured speedup (a plain loop 9 to 10 times julia's own interpreter, down from
15; Base built in 212 s, down from about 340 s), which are the maintainers'
indicative figures. It gives what the
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

# dynamic-monorepo demo

A small polyglot monorepo (Node, Go and Docker) that uses
[Continuous-Actions/dynamic-monorepo](https://github.com/Continuous-Actions/dynamic-monorepo)
with **no configuration file**. The [CI workflow](.github/workflows/ci.yml) is the whole setup.

```text
libs/shared      (node)  ◀── services/api (node + Dockerfile)
                         ◀── apps/web     (node)
libs/geo         (go)    ◀── services/worker (go + Dockerfile)
```

## See it work

Each pull request below changes one thing. Open its **Checks → CI → Summary** to see what was selected and why.

| Pull request | Change | What runs |
| --- | --- | --- |
| *shared library* | `libs/shared/index.js` | build: shared, api, web · docker: api |
| *worker Dockerfile* | `services/worker/Dockerfile` | build + docker: worker |
| *Go library* | `libs/geo/geo.go` | build: geo, worker · docker: worker |
| *docs only* | `README.md` | nothing (all jobs skipped) |

Try it yourself: fork this repository, change a file, and open a pull request.

_Docs-only change: nothing should build._

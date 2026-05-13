I'm Charlie, a software engineer interested in systems, real-time infrastructure, and developer tooling. I work mostly in TypeScript and Go, with some Python and Rust mixed in.

Currently looking for software engineering internships or full-time roles.

## Open Source

| Repo | PR | Status |
|------|-----|--------|
| [tailscale/tailscale](https://github.com/tailscale/tailscale) | [Wrap ACME errors with more context for cert timeouts #19688](https://github.com/tailscale/tailscale/pull/19688) | Open |
| [tailscale/tailscale](https://github.com/tailscale/tailscale) | [Require /etc/synoinfo.conf for Synology distro detection #19689](https://github.com/tailscale/tailscale/pull/19689) | Open |
| [tailscale/tailscale](https://github.com/tailscale/tailscale) | [Don't emit broken hint for invalid legacy tcp serve args #19690](https://github.com/tailscale/tailscale/pull/19690) | Open |
| [livekit/server-sdk-go](https://github.com/livekit/server-sdk-go) | [cloudagents: increase scanner buffer to avoid token too long errors #903](https://github.com/livekit/server-sdk-go/pull/903) | Open |
| [livekit/livekit-cli](https://github.com/livekit/livekit-cli) | [Add --id flag to agent deploy command #839](https://github.com/livekit/livekit-cli/pull/839) | Open |
| [livekit/livekit-cli](https://github.com/livekit/livekit-cli) | [install: create GOBIN directory if it doesn't exist #840](https://github.com/livekit/livekit-cli/pull/840) | Open |
| [livekit/livekit-cli](https://github.com/livekit/livekit-cli) | [token create: don't show default localhost URL in output #841](https://github.com/livekit/livekit-cli/pull/841) | Open |
| [livekit/livekit-cli](https://github.com/livekit/livekit-cli) | [agentfs: use forward slashes in Dockerfile entrypoint paths on Windows #842](https://github.com/livekit/livekit-cli/pull/842) | Open |
| [hashicorp/go-retryablehttp](https://github.com/hashicorp/go-retryablehttp) | [Don't start backoff timer if it would exceed context deadline #284](https://github.com/hashicorp/go-retryablehttp/pull/284) | Open |
| [jackc/pgx](https://github.com/jackc/pgx) | [pgconn: use fresh context for fallback connection in connectPreferred #2554](https://github.com/jackc/pgx/pull/2554) | Open |
| [jackc/pgx](https://github.com/jackc/pgx) | [pgconn: preserve full error chain in normalizeTimeoutError #2556](https://github.com/jackc/pgx/pull/2556) | Open |
| [compose-spec/compose-go](https://github.com/compose-spec/compose-go) | [types: add Options field to IPAMConfig #870](https://github.com/compose-spec/compose-go/pull/870) | Open |
| [etcd-io/etcd](https://github.com/etcd-io/etcd) | [clientv3: don't log warn/error for expected context cancellation on shutdown #21739](https://github.com/etcd-io/etcd/pull/21739) | Open |
| [grpc/grpc-go](https://github.com/grpc/grpc-go) | [stats/opentelemetry: set ai.method in clientTracingHandler.TagRPC #9116](https://github.com/grpc/grpc-go/pull/9116) | Open |
| [launchbadge/sqlx](https://github.com/launchbadge/sqlx) | [sqlx-cli: use cyan instead of white for help text literals #4263](https://github.com/launchbadge/sqlx/pull/4263) | Open |
| [jmoiron/sqlx](https://github.com/jmoiron/sqlx) | [In: skip ? inside SQL comments and string literals #984](https://github.com/jmoiron/sqlx/pull/984) | Open |
| [spf13/afero](https://github.com/spf13/afero) | [MemMapFs: Mkdir now errors when the parent directory doesn't exist #599](https://github.com/spf13/afero/pull/599) | Open |
| [nats-io/nats.go](https://github.com/nats-io/nats.go) | [kv: reject keys with consecutive dots in keyValid and searchKeyValid #2076](https://github.com/nats-io/nats.go/pull/2076) | Open |
| [hashicorp/hcl](https://github.com/hashicorp/hcl) | [hclsyntax: fix body SrcRange start when file begins with a comment #797](https://github.com/hashicorp/hcl/pull/797) | Open |
| [pterm/pterm](https://github.com/pterm/pterm) | [fix: BasicTextPrinter.Sprintln appends two newlines instead of one #784](https://github.com/pterm/pterm/pull/784) | Open |
| [google/uuid](https://github.com/google/uuid) | [null: fix NullUUID.Scan returning Valid=true for empty string/bytes #216](https://github.com/google/uuid/pull/216) | Open |
| [charmbracelet/log](https://github.com/charmbracelet/log) | [Share level pointer so child loggers inherit parent level changes #209](https://github.com/charmbracelet/log/pull/209) | Open |
| [charmbracelet/bubbles](https://github.com/charmbracelet/bubbles) | [list: fix RemoveItem using wrong index when a filter is active #970](https://github.com/charmbracelet/bubbles/pull/970) | Open |
| [uber-go/goleak](https://github.com/uber-go/goleak) | [IgnoreAnyFunction: also check the created-by frame #143](https://github.com/uber-go/goleak/pull/143) | Open |
| [charmbracelet/huh](https://github.com/charmbracelet/huh) | [Scope navigation messages to their originating form #778](https://github.com/charmbracelet/huh/pull/778) | Open |
| [rs/zerolog](https://github.com/rs/zerolog) | [ctx: propagate Go context to events created via Ctx(ctx) #769](https://github.com/rs/zerolog/pull/769) | Open |

## Projects

**[agent-eval](https://github.com/c-tonneslan/agent-eval)** — From-scratch LLM agent evaluation framework. Rolls a bare ReAct loop with the Anthropic SDK (no LangChain), runs 21 tasks across web browsing, code debugging, and multi-step tool use, and scores with a mix of exact match, code test execution, and LLM-as-judge. Includes trajectory logging, failure mode classification, an HTML dashboard, and a calibration tool that computes Pearson r between judge and human scores. TypeScript.

## Links

- [c-tonneslan-portfolio.vercel.app](https://c-tonneslan-portfolio.vercel.app)
- cst0520@gmail.com

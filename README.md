I'm Charlie. Software engineer. The work I keep coming back to is civic and urban: housing, zoning, transit, civil infrastructure, and the policy that shapes them. Mostly Go and TypeScript day-to-day, with Python and Rust on the side. Plenty of backend and developer tooling work too. I read other people's code for fun, which is how most of the bugs below got found.

Open to remote software engineering roles, especially anywhere code meets cities, planning, or public infrastructure. Reach me at cst0520@gmail.com.

## Merged contributions

Bugs and features I shipped into widely-used Go libraries:

- **[jackc/pgx](https://github.com/jackc/pgx)** ([#2554](https://github.com/jackc/pgx/pull/2554), [#2556](https://github.com/jackc/pgx/pull/2556), [#2559](https://github.com/jackc/pgx/pull/2559)). Postgres driver for Go. Fixed a context leak where `connectPreferred`'s fallback dial inherited the already-expired deadline. Preserved the full error chain across `normalizeTimeoutError` so callers can `errors.Unwrap` to the real cause. Added an `ErrConnClosed` sentinel so callers can `errors.Is` the closed-pool case. Three PRs, three merges, all reviewed by jackc.
- **[wailsapp/wails](https://github.com/wailsapp/wails)** ([#5468](https://github.com/wailsapp/wails/pull/5468)). Go + WebView desktop framework. Nil-guarded `Application.Quit` so calling it before `Run()` no longer panics the host app on early shutdown.
- **[nats-io/nats.go](https://github.com/nats-io/nats.go)** ([#2076](https://github.com/nats-io/nats.go/pull/2076)). NATS client for Go. Tightened the JetStream KV key validator so consecutive dots stop sneaking past `keyValid` and `searchKeyValid`, which had been quietly producing unreadable keys.
- **[urfave/cli](https://github.com/urfave/cli)** ([#2328](https://github.com/urfave/cli/pull/2328)). Most-used CLI framework in Go. Pinned down the empty-positional-after-flag case with a regression test I ran into writing a different tool.
- **[gocolly/colly](https://github.com/gocolly/colly)** ([#873](https://github.com/gocolly/colly/pull/873)). Web scraping framework. Dropped a deprecated `rand.Seed` call from `httpBackend.Init` that started warning under Go 1.20+.

Open and in review: ~215 more PRs across ~140 repos, including Tailscale, LiveKit, gRPC, etcd, Charm, Grafana k6, OpenTelemetry, sqlx, asynq, chi, kong, fx, atomic, goleak, golang-jwt, go-jose, go-yaml, gleam, uutils/coreutils, cross-rs, rust-itertools, mySociety (MapIt, FixMyStreet, Alaveteli, TheyWorkForYou), DemocracyClub, Open States, OpenElections, NYCDB, and more. Full list collapsed at the bottom.

<details>
<summary>All PRs (open and merged)</summary>

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
| [jackc/pgx](https://github.com/jackc/pgx) | [pgconn: use fresh context for fallback connection in connectPreferred #2554](https://github.com/jackc/pgx/pull/2554) | Merged |
| [jackc/pgx](https://github.com/jackc/pgx) | [pgconn: preserve full error chain in normalizeTimeoutError #2556](https://github.com/jackc/pgx/pull/2556) | Merged |
| [compose-spec/compose-go](https://github.com/compose-spec/compose-go) | [types: add Options field to IPAMConfig #870](https://github.com/compose-spec/compose-go/pull/870) | Open |
| [etcd-io/etcd](https://github.com/etcd-io/etcd) | [clientv3: don't log warn/error for expected context cancellation on shutdown #21739](https://github.com/etcd-io/etcd/pull/21739) | Open |
| [grpc/grpc-go](https://github.com/grpc/grpc-go) | [stats/opentelemetry: set ai.method in clientTracingHandler.TagRPC #9116](https://github.com/grpc/grpc-go/pull/9116) | Open |
| [launchbadge/sqlx](https://github.com/launchbadge/sqlx) | [sqlx-cli: use cyan instead of white for help text literals #4263](https://github.com/launchbadge/sqlx/pull/4263) | Open |
| [jmoiron/sqlx](https://github.com/jmoiron/sqlx) | [In: skip ? inside SQL comments and string literals #984](https://github.com/jmoiron/sqlx/pull/984) | Open |
| [jmoiron/sqlx](https://github.com/jmoiron/sqlx) | [named: support PostgreSQL :: cast directly after a named param #985](https://github.com/jmoiron/sqlx/pull/985) | Open |
| [spf13/afero](https://github.com/spf13/afero) | [MemMapFs: Mkdir now errors when the parent directory doesn't exist #599](https://github.com/spf13/afero/pull/599) | Open |
| [nats-io/nats.go](https://github.com/nats-io/nats.go) | [kv: reject keys with consecutive dots in keyValid and searchKeyValid #2076](https://github.com/nats-io/nats.go/pull/2076) | Merged |
| [pterm/pterm](https://github.com/pterm/pterm) | [fix: BasicTextPrinter.Sprintln appends two newlines instead of one #784](https://github.com/pterm/pterm/pull/784) | Open |
| [pterm/pterm](https://github.com/pterm/pterm) | [fix: InteractiveMultiselect right arrow selects only filtered options #785](https://github.com/pterm/pterm/pull/785) | Open |
| [pterm/pterm](https://github.com/pterm/pterm) | [fix(spinner): remove data race on SpinnerPrinter IsActive and Text #786](https://github.com/pterm/pterm/pull/786) | Open |
| [pterm/pterm](https://github.com/pterm/pterm) | [fix(table): use unicode vertical bar in default Separator #787](https://github.com/pterm/pterm/pull/787) | Open |
| [google/uuid](https://github.com/google/uuid) | [null: fix NullUUID.Scan returning Valid=true for empty string/bytes #216](https://github.com/google/uuid/pull/216) | Open |
| [charmbracelet/log](https://github.com/charmbracelet/log) | [Share level pointer so child loggers inherit parent level changes #209](https://github.com/charmbracelet/log/pull/209) | Open |
| [charmbracelet/log](https://github.com/charmbracelet/log) | [fix: share mutex between a logger and its With() clones #210](https://github.com/charmbracelet/log/pull/210) | Open |
| [charmbracelet/log](https://github.com/charmbracelet/log) | [fix: don't drop user keyvals named like reserved keys #211](https://github.com/charmbracelet/log/pull/211) | Open |
| [charmbracelet/bubbles](https://github.com/charmbracelet/bubbles) | [list: fix RemoveItem using wrong index when a filter is active #970](https://github.com/charmbracelet/bubbles/pull/970) | Open |
| [charmbracelet/bubbles](https://github.com/charmbracelet/bubbles) | [fix(textinput): stop applying Text/Placeholder style to padding #973](https://github.com/charmbracelet/bubbles/pull/973) | Open |
| [charmbracelet/bubbles](https://github.com/charmbracelet/bubbles) | [fix(textarea): stop wordLeft from spinning on an empty buffer #974](https://github.com/charmbracelet/bubbles/pull/974) | Open |
| [charmbracelet/bubbles](https://github.com/charmbracelet/bubbles) | [textinput: render the full placeholder when Width is 0 #976](https://github.com/charmbracelet/bubbles/pull/976) | Open |
| [uber-go/goleak](https://github.com/uber-go/goleak) | [IgnoreAnyFunction: also check the created-by frame #143](https://github.com/uber-go/goleak/pull/143) | Open |
| [uber-go/goleak](https://github.com/uber-go/goleak) | [filter: add default filter for the pure-Go DNS resolver #144](https://github.com/uber-go/goleak/pull/144) | Open |
| [uber-go/goleak](https://github.com/uber-go/goleak) | [docs(IgnoreCurrent): warn that the snapshot happens at call time #145](https://github.com/uber-go/goleak/pull/145) | Open |
| [charmbracelet/huh](https://github.com/charmbracelet/huh) | [Scope navigation messages to their originating form #778](https://github.com/charmbracelet/huh/pull/778) | Open |
| [charmbracelet/lipgloss](https://github.com/charmbracelet/lipgloss) | [GetBorder* bool getters return true when only BorderStyle is set #675](https://github.com/charmbracelet/lipgloss/pull/675) | Open |
| [charmbracelet/lipgloss](https://github.com/charmbracelet/lipgloss) | [fix(tree): stop swapping Offset start and end #676](https://github.com/charmbracelet/lipgloss/pull/676) | Open |
| [charmbracelet/lipgloss](https://github.com/charmbracelet/lipgloss) | [collapse newlines to spaces in inline mode #680](https://github.com/charmbracelet/lipgloss/pull/680) | Open |
| [fatih/color](https://github.com/fatih/color) | [fix: correct AddBgRGB godoc and tighten both RGB examples #287](https://github.com/fatih/color/pull/287) | Open |
| [lima-vm/lima](https://github.com/lima-vm/lima) | [docs: document missing LIMA_CIDATA_* env vars #4988](https://github.com/lima-vm/lima/pull/4988) | Open |
| [uber-go/atomic](https://github.com/uber-go/atomic) | [atomic.Time: add MarshalJSON / UnmarshalJSON #208](https://github.com/uber-go/atomic/pull/208) | Open |
| [uber-go/atomic](https://github.com/uber-go/atomic) | [use CompareAndSwap instead of the deprecated CAS shim internally #209](https://github.com/uber-go/atomic/pull/209) | Open |
| [charmbracelet/skate](https://github.com/charmbracelet/skate) | [feat(list): show single-line previews for long/multiline values #177](https://github.com/charmbracelet/skate/pull/177) | Open |
| [charmbracelet/glamour](https://github.com/charmbracelet/glamour) | [fix(ansi): honor Conceal in renderText #550](https://github.com/charmbracelet/glamour/pull/550) | Open |
| [charmbracelet/glamour](https://github.com/charmbracelet/glamour) | [fix(ansi): handle all CommonMark backslash escapes #551](https://github.com/charmbracelet/glamour/pull/551) | Open |
| [rs/cors](https://github.com/rs/cors) | [docs: point Martini link at the active repo #214](https://github.com/rs/cors/pull/214) | Open |
| [charmbracelet/ssh](https://github.com/charmbracelet/ssh) | [docs: replace dead Gliderlabs Slack link with Charm Discord #42](https://github.com/charmbracelet/ssh/pull/42) | Open |
| [tsenart/vegeta](https://github.com/tsenart/vegeta) | [docs: point TDigest reference at javadoc.io #761](https://github.com/tsenart/vegeta/pull/761) | Open |
| [bradleyjkemp/cupaloy](https://github.com/bradleyjkemp/cupaloy) | [fix: scrub Go-module-path-invalid chars from snapshot filenames #89](https://github.com/bradleyjkemp/cupaloy/pull/89) | Open |
| [go-kit/kit](https://github.com/go-kit/kit) | [all: replace deprecated io/ioutil usage #1312](https://github.com/go-kit/kit/pull/1312) | Open |
| [urfave/cli](https://github.com/urfave/cli) | [test: regression for empty positional arg after a flag #2328](https://github.com/urfave/cli/pull/2328) | Merged |
| [urfave/cli](https://github.com/urfave/cli) | [inherit Reader/Writer/ErrWriter from parent on subcommand setup #2329](https://github.com/urfave/cli/pull/2329) | Open |
| [urfave/cli](https://github.com/urfave/cli) | [v3: yield the version flag's -v alias to a user-defined flag #2330](https://github.com/urfave/cli/pull/2330) | Open |
| [go-jose/go-jose](https://github.com/go-jose/go-jose) | [json: report actual JSON kind in UnmarshalText type errors #232](https://github.com/go-jose/go-jose/pull/232) | Open |
| [goccy/go-yaml](https://github.com/goccy/go-yaml) | [parser: keep grouping trailing documents after adjacent --- #877](https://github.com/goccy/go-yaml/pull/877) | Open |
| [gorilla/schema](https://github.com/gorilla/schema) | [decoder: don't panic when path crosses an unexported pointer field #243](https://github.com/gorilla/schema/pull/243) | Open |
| [gorilla/csrf](https://github.com/gorilla/csrf) | [csrf: reject Origin: null as an opaque origin #207](https://github.com/gorilla/csrf/pull/207) | Open |
| [gorilla/sessions](https://github.com/gorilla/sessions) | [registry: don't panic when store.New returns a nil session #291](https://github.com/gorilla/sessions/pull/291) | Open |
| [go-rod/rod](https://github.com/go-rod/rod) | [fix: clear per-session CDP states when a page closes #1235](https://github.com/go-rod/rod/pull/1235) | Open |
| [gocolly/colly](https://github.com/gocolly/colly) | [drop deprecated rand.Seed call in httpBackend.Init #873](https://github.com/gocolly/colly/pull/873) | Merged |
| [kataras/iris](https://github.com/kataras/iris) | [docs: fix broken Movies Service link in _examples README #2606](https://github.com/kataras/iris/pull/2606) | Open |
| [mingrammer/flog](https://github.com/mingrammer/flog) | [drop deprecated rand.Seed call in main #70](https://github.com/mingrammer/flog/pull/70) | Open |
| [valyala/fastjson](https://github.com/valyala/fastjson) | [util: replace deprecated reflect.StringHeader/SliceHeader #121](https://github.com/valyala/fastjson/pull/121) | Open |
| [aymanbagabas/go-pty](https://github.com/aymanbagabas/go-pty) | [cmd_windows: return *exec.ExitError on non-zero exit #50](https://github.com/aymanbagabas/go-pty/pull/50) | Merged |
| [bsm/redislock](https://github.com/bsm/redislock) | [obtain: wrap ctx error with ErrNotObtained when retry deadline hits #84](https://github.com/bsm/redislock/pull/84) | Open |
| [chasefleming/elem-go](https://github.com/chasefleming/elem-go) | [feat: add Wbr element constructor #175](https://github.com/chasefleming/elem-go/pull/175) | Open |
| [chasefleming/elem-go](https://github.com/chasefleming/elem-go) | [feat: add Track element constructor #176](https://github.com/chasefleming/elem-go/pull/176) | Open |
| [chasefleming/elem-go](https://github.com/chasefleming/elem-go) | [feat: add Picture element constructor #177](https://github.com/chasefleming/elem-go/pull/177) | Open |
| [chasefleming/elem-go](https://github.com/chasefleming/elem-go) | [feat: add Bdi and Bdo element constructors #178](https://github.com/chasefleming/elem-go/pull/178) | Open |
| [chasefleming/elem-go](https://github.com/chasefleming/elem-go) | [feat(attrs): add ClassNames helper for conditional class lists #179](https://github.com/chasefleming/elem-go/pull/179) | Open |
| [r3labs/sse](https://github.com/r3labs/sse) | [test: poll goroutine count to deflake TestSubscribeWithContextDone #191](https://github.com/r3labs/sse/pull/191) | Open |
| [muesli/mango](https://github.com/muesli/mango) | [feat: honor SOURCE_DATE_EPOCH for the man page heading timestamp #28](https://github.com/muesli/mango/pull/28) | Open |
| [muesli/gamut](https://github.com/muesli/gamut) | [palette: switch Color literals to keyed form to silence go vet #26](https://github.com/muesli/gamut/pull/26) | Open |
| [muesli/gitcha](https://github.com/muesli/gitcha) | [fix: don't ignore-match the root path itself in FindFiles #9](https://github.com/muesli/gitcha/pull/9) | Open |
| [coreos/go-iptables](https://github.com/coreos/go-iptables) | [iptables: return error from ListById when chain has no matching rule #136](https://github.com/coreos/go-iptables/pull/136) | Open |
| [fatih/structtag](https://github.com/fatih/structtag) | [export sentinel errors so callers can use errors.Is #27](https://github.com/fatih/structtag/pull/27) | Open |
| [fatih/structtag](https://github.com/fatih/structtag) | [docs: rewrite Tags.Get doc comment #28](https://github.com/fatih/structtag/pull/28) | Open |
| [bwmarrin/discordgo](https://github.com/bwmarrin/discordgo) | [fix: nil-check wsConn in Op1 heartbeat and ChannelVoiceJoinManual #1719](https://github.com/bwmarrin/discordgo/pull/1719) | Open |
| [go-playground/locales](https://github.com/go-playground/locales) | [docs: clarify Ordinal/CardinalPluralRule README example output #51](https://github.com/go-playground/locales/pull/51) | Open |
| [alexedwards/scs](https://github.com/alexedwards/scs) | [gormstore: export Session for callers using custom migration tooling #263](https://github.com/alexedwards/scs/pull/263) | Open |
| [rs/xid](https://github.com/rs/xid) | [docs(NewWithTime): note 4-byte timestamp can't hold post-2106 times #116](https://github.com/rs/xid/pull/116) | Open |
| [coreos/go-oidc](https://github.com/coreos/go-oidc) | [oidc: expose typed error and sentinel for issuer-mismatch failures #481](https://github.com/coreos/go-oidc/pull/481) | Open |
| [go-playground/validator](https://github.com/go-playground/validator) | [Anchor cron regex so substrings can't pass validation #1578](https://github.com/go-playground/validator/pull/1578) | Open |
| [mattn/go-sqlite3](https://github.com/mattn/go-sqlite3) | [Fix wrong arg count in Exec's "not enough args" error #1398](https://github.com/mattn/go-sqlite3/pull/1398) | Open |
| [jackc/pgx](https://github.com/jackc/pgx) | [pgconn: add ErrConnClosed sentinel and unwrap it from connLockError #2559](https://github.com/jackc/pgx/pull/2559) | Merged |
| [samber/lo](https://github.com/samber/lo) | [mutable: fix wrong/misleading doc comments on Filter, FilterI, Map, MapI #888](https://github.com/samber/lo/pull/888) | Open |
| [charmbracelet/x](https://github.com/charmbracelet/x) | [ansi: document that StringWidth treats tabs as zero width #864](https://github.com/charmbracelet/x/pull/864) | Open |
| [charmbracelet/x](https://github.com/charmbracelet/x) | [fix(ansi): emit DECSWT/DECSIN with correct OSC numbers and ST #865](https://github.com/charmbracelet/x/pull/865) | Open |
| [samber/lo](https://github.com/samber/lo) | [docs(concat): example uses lo.Concat, not lo.Flatten #889](https://github.com/samber/lo/pull/889) | Open |
| [dustin/go-humanize](https://github.com/dustin/go-humanize) | [si: accept the Greek letter mu as an alias for µ in ParseSI #150](https://github.com/dustin/go-humanize/pull/150) | Open |
| [goccy/go-yaml](https://github.com/goccy/go-yaml) | [printer: check Alias not Anchor in the AliasType branch #879](https://github.com/goccy/go-yaml/pull/879) | Open |
| [goccy/go-yaml](https://github.com/goccy/go-yaml) | [ast: keep trailing blank lines when rendering \|+ literals #880](https://github.com/goccy/go-yaml/pull/880) | Open |
| [goccy/go-yaml](https://github.com/goccy/go-yaml) | [playground: add Docs link to pkg.go.dev #881](https://github.com/goccy/go-yaml/pull/881) | Open |
| [pelletier/go-toml](https://github.com/pelletier/go-toml) | [marshaler: respect TextMarshaler when checking omitempty on structs #1060](https://github.com/pelletier/go-toml/pull/1060) | Open |
| [samber/lo](https://github.com/samber/lo) | [mutable: zero out tail slots dropped by Filter and FilterI #890](https://github.com/samber/lo/pull/890) | Open |
| [sashabaranov/go-openai](https://github.com/sashabaranov/go-openai) | [stream_reader: stop wrapping nil APIError into "error, <nil>" #1107](https://github.com/sashabaranov/go-openai/pull/1107) | Open |
| [sashabaranov/go-openai](https://github.com/sashabaranov/go-openai) | [form_builder: always set a Content-Type on reader-based form parts #1108](https://github.com/sashabaranov/go-openai/pull/1108) | Open |
| [caarlos0/env](https://github.com/caarlos0/env) | [respect env values over non-zero fields under SetDefaultsForZeroValuesOnly #420](https://github.com/caarlos0/env/pull/420) | Open |
| [caarlos0/env](https://github.com/caarlos0/env) | [feat: AllowEmpty option to keep empty env values instead of defaults #421](https://github.com/caarlos0/env/pull/421) | Open |
| [charmbracelet/fang](https://github.com/charmbracelet/fang) | [style the --version output to match the rest of fang #98](https://github.com/charmbracelet/fang/pull/98) | Open |
| [charmbracelet/fang](https://github.com/charmbracelet/fang) | [style 'unknown help topic' errors #99](https://github.com/charmbracelet/fang/pull/99) | Open |
| [bradfitz/gomemcache](https://github.com/bradfitz/gomemcache) | [Ping returns ErrNoServers when no servers are configured #195](https://github.com/bradfitz/gomemcache/pull/195) | Open |
| [go-chi/chi](https://github.com/go-chi/chi) | [middleware: thread useColor through Panic so NoColor logger emits plain text #1094](https://github.com/go-chi/chi/pull/1094) | Open |
| [go-chi/chi](https://github.com/go-chi/chi) | [middleware: GetHead advertises HEAD in the 405 Allow header #1095](https://github.com/go-chi/chi/pull/1095) | Open |
| [go-chi/chi](https://github.com/go-chi/chi) | [mux: dedupe the Allow header on 405 responses #1096](https://github.com/go-chi/chi/pull/1096) | Open |
| [xeipuuv/gojsonschema](https://github.com/xeipuuv/gojsonschema) | [schema: fix copy-paste typo in allOf-must-be-array error #388](https://github.com/xeipuuv/gojsonschema/pull/388) | Open |
| [cli/go-gh](https://github.com/cli/go-gh) | [browser: handle launcher paths that contain spaces #223](https://github.com/cli/go-gh/pull/223) | Open |
| [golang-migrate/migrate](https://github.com/golang-migrate/migrate) | [postgres/pgx: don't leak the conn from WithInstance when init fails #1397](https://github.com/golang-migrate/migrate/pull/1397) | Open |
| [vouch/vouch-proxy](https://github.com/vouch/vouch-proxy) | [cfg: respect VOUCH_LOGLEVEL when no config file value is set #610](https://github.com/vouch/vouch-proxy/pull/610) | Open |
| [rclone/rclone](https://github.com/rclone/rclone) | [operations: fix DeleteFile godoc, it doesn't honor --backup-dir #9440](https://github.com/rclone/rclone/pull/9440) | Open |
| [mholt/archives](https://github.com/mholt/archives) | [fs: make ArchiveFS.Sub return a new FS rooted at the joined prefix #70](https://github.com/mholt/archives/pull/70) | Open |
| [chzyer/readline](https://github.com/chzyer/readline) | [example/readline-demo: add missing os import #265](https://github.com/chzyer/readline/pull/265) | Open |
| [hibiken/asynq](https://github.com/hibiken/asynq) | [recover from panics in user-provided callbacks #1134](https://github.com/hibiken/asynq/pull/1134) | Open |
| [hibiken/asynq](https://github.com/hibiken/asynq) | [scheduler: don't log shared-connection close as an error #1135](https://github.com/hibiken/asynq/pull/1135) | Open |
| [alecthomas/kong](https://github.com/alecthomas/kong) | [allow ${env} in the help template of a positional argument #599](https://github.com/alecthomas/kong/pull/599) | Open |
| [alecthomas/kong](https://github.com/alecthomas/kong) | [fire AfterApply for env-only flags #600](https://github.com/alecthomas/kong/pull/600) | Merged |
| [uber-go/fx](https://github.com/uber-go/fx) | [fix the error example to pass a constructor to fx.Provide #1290](https://github.com/uber-go/fx/pull/1290) | Open |
| [muesli/reflow](https://github.com/muesli/reflow) | [dedent: respect zero-indent lines when computing the shared indent #83](https://github.com/muesli/reflow/pull/83) | Open |
| [valyala/quicktemplate](https://github.com/valyala/quicktemplate) | [docs: install qtc via go install instead of the dropped go get -u #106](https://github.com/valyala/quicktemplate/pull/106) | Open |
| [Masterminds/sprig](https://github.com/Masterminds/sprig) | [add a test for the mod helper #478](https://github.com/Masterminds/sprig/pull/478) | Open |
| [Masterminds/sprig](https://github.com/Masterminds/sprig) | [docs: clarify that seq returns a string, not an integer slice #479](https://github.com/Masterminds/sprig/pull/479) | Open |
| [go-task/slim-sprig](https://github.com/go-task/slim-sprig) | [drop deprecated rand.Seed init hook #24](https://github.com/go-task/slim-sprig/pull/24) | Open |
| [tucnak/telebot](https://github.com/tucnak/telebot) | [errors: redact bot token from wrapped transport errors #809](https://github.com/tucnak/telebot/pull/809) | Merged |
| [tucnak/telebot](https://github.com/tucnak/telebot) | [fix(file): default the multipart filename to the on-disk basename #810](https://github.com/tucnak/telebot/pull/810) | Merged |
| [tursodatabase/turso-cli](https://github.com/tursodatabase/turso-cli) | [db unarchive: suggest the group unarchive command when applicable #1041](https://github.com/tursodatabase/turso-cli/pull/1041) | Open |
| [tursodatabase/turso-cli](https://github.com/tursodatabase/turso-cli) | [from-csv: print sqlite's stderr as text instead of hex #1042](https://github.com/tursodatabase/turso-cli/pull/1042) | Open |
| [tursodatabase/turso-cli](https://github.com/tursodatabase/turso-cli) | [db create: derive group from source db when forking #1043](https://github.com/tursodatabase/turso-cli/pull/1043) | Open |
| [tursodatabase/turso-cli](https://github.com/tursodatabase/turso-cli) | [csv-table-name: reject invalid SQLite identifiers up front #1044](https://github.com/tursodatabase/turso-cli/pull/1044) | Open |
| [wagslane/go-rabbitmq](https://github.com/wagslane/go-rabbitmq) | [options: merge queue and exchange args instead of replacing #213](https://github.com/wagslane/go-rabbitmq/pull/213) | Open |
| [gomarkdown/markdown](https://github.com/gomarkdown/markdown) | [docs: drop the dead Try it online link #360](https://github.com/gomarkdown/markdown/pull/360) | Open |
| [go-jose/go-jose](https://github.com/go-jose/go-jose) | [preserve the original protected header bytes when re-serializing a JWS #233](https://github.com/go-jose/go-jose/pull/233) | Open |
| [go-jose/go-jose](https://github.com/go-jose/go-jose) | [remove bare returns outside the json/ fork #234](https://github.com/go-jose/go-jose/pull/234) | Open |
| [charmbracelet/freeze](https://github.com/charmbracelet/freeze) | [expand --output path so '~' and relative paths land where users expect #267](https://github.com/charmbracelet/freeze/pull/267) | Open |
| [charmbracelet/freeze](https://github.com/charmbracelet/freeze) | [help: swap JoinHorizontal/JoinVertical position arguments #268](https://github.com/charmbracelet/freeze/pull/268) | Open |
| [simonw/sqlite-utils](https://github.com/simonw/sqlite-utils) | [Don't transform empty CSV table that was never created #736](https://github.com/simonw/sqlite-utils/pull/736) | Open |
| [simonw/sqlite-utils](https://github.com/simonw/sqlite-utils) | [docs: render --convert and --functions literally in install section #737](https://github.com/simonw/sqlite-utils/pull/737) | Open |
| [rust-bakery/nom](https://github.com/rust-bakery/nom) | [tests: make issue_848 overflow test portable to 32-bit usize #1881](https://github.com/rust-bakery/nom/pull/1881) | Open |
| [rust-itertools/itertools](https://github.com/rust-itertools/itertools) | [take_while_inclusive: tighten FusedIterator to require I: FusedIterator #1101](https://github.com/rust-itertools/itertools/pull/1101) | Open |
| [rust-itertools/itertools](https://github.com/rust-itertools/itertools) | [InterleaveShortest: don't overflow size_hint lower bound #1102](https://github.com/rust-itertools/itertools/pull/1102) | Open |
| [rust-itertools/itertools](https://github.com/rust-itertools/itertools) | [PeekNth: don't panic on peek_nth(usize::MAX) #1103](https://github.com/rust-itertools/itertools/pull/1103) | Open |
| [go-redis/cache](https://github.com/go-redis/cache) | [local: clamp tinylfu cache size to avoid panic at size 1 or 2 #112](https://github.com/go-redis/cache/pull/112) | Open |
| [go-redis/cache](https://github.com/go-redis/cache) | [export rediser interface as Rediser #113](https://github.com/go-redis/cache/pull/113) | Open |
| [cookiecutter/cookiecutter](https://github.com/cookiecutter/cookiecutter) | [generate: keep applying overrides after the first invalid one #2223](https://github.com/cookiecutter/cookiecutter/pull/2223) | Open |
| [launchbadge/sqlx](https://github.com/launchbadge/sqlx) | [sqlx-cli: read confirmation as a plain line, not a raw-mode toggle #4268](https://github.com/launchbadge/sqlx/pull/4268) | Open |
| [wailsapp/wails](https://github.com/wailsapp/wails) | [v2: nil-guard Application.Quit so pre-Run shutdown doesn't panic #5468](https://github.com/wailsapp/wails/pull/5468) | Merged |
| [grafana/k6](https://github.com/grafana/k6) | [fix: trim trailing slashes from cloud login stack URL #6001](https://github.com/grafana/k6/pull/6001) | Open |
| [charmbracelet/colorprofile](https://github.com/charmbracelet/colorprofile) | [env: honor COLORTERM=truecolor inside tmux #83](https://github.com/charmbracelet/colorprofile/pull/83) | Open |
| [charmbracelet/pop](https://github.com/charmbracelet/pop) | [allow SMTP without credentials for anonymous relays #167](https://github.com/charmbracelet/pop/pull/167) | Open |
| [charmbracelet/soft-serve](https://github.com/charmbracelet/soft-serve) | [serve: don't drop the server start error on the way out #889](https://github.com/charmbracelet/soft-serve/pull/889) | Open |
| [charmbracelet/glow](https://github.com/charmbracelet/glow) | [include pager stderr in --pager failure messages #948](https://github.com/charmbracelet/glow/pull/948) | Open |
| [charmbracelet/glow](https://github.com/charmbracelet/glow) | [fix: expand ~ in style path from glow.yml #949](https://github.com/charmbracelet/glow/pull/949) | Open |
| [charmbracelet/gum](https://github.com/charmbracelet/gum) | [fix(spin): drain PTY copy goroutines before reading stdout/stderr #1075](https://github.com/charmbracelet/gum/pull/1075) | Open |
| [charmbracelet/vhs](https://github.com/charmbracelet/vhs) | [kill ttyd on early Evaluate exit and on Start failure #752](https://github.com/charmbracelet/vhs/pull/752) | Open |
| [golang-jwt/jwt](https://github.com/golang-jwt/jwt) | [mapclaims: stop treating exp=0 as a missing claim #509](https://github.com/golang-jwt/jwt/pull/509) | Open |
| [go-ldap/ldap](https://github.com/go-ldap/ldap) | [v3/control: replace unchecked type asserts in DecodeControl with comma-ok #589](https://github.com/go-ldap/ldap/pull/589) | Merged |
| [go-ldap/ldap](https://github.com/go-ldap/ldap) | [fix(conn): parse ldapi:// URLs per RFC 4516 #590](https://github.com/go-ldap/ldap/pull/590) | Merged |
| [cli/cli](https://github.com/cli/cli) | [docs: drop --repo gh-cli from dnf install lines #13444](https://github.com/cli/cli/pull/13444) | Merged |
| [emersion/go-imap](https://github.com/emersion/go-imap) | [imapclient: don't tear down the connection on dynamic COPYUID #755](https://github.com/emersion/go-imap/pull/755) | Open |
| [open-telemetry/opentelemetry-go-contrib](https://github.com/open-telemetry/opentelemetry-go-contrib) | [detectors/hetzner: respect context in Detect #8999](https://github.com/open-telemetry/opentelemetry-go-contrib/pull/8999) | Open |
| [hetznercloud/hcloud-go](https://github.com/hetznercloud/hcloud-go) | [metadata: add context-aware Client methods #852](https://github.com/hetznercloud/hcloud-go/pull/852) | Merged |
| [uutils/coreutils](https://github.com/uutils/coreutils) | [sort: don't accept leading '+' in numeric (-n) sort #12336](https://github.com/uutils/coreutils/pull/12336) | Open |
| [uutils/coreutils](https://github.com/uutils/coreutils) | [more: swap -f and -l short flags to match GNU/util-linux #12337](https://github.com/uutils/coreutils/pull/12337) | Open |
| [uutils/coreutils](https://github.com/uutils/coreutils) | [chmod: report Permission denied instead of No such file when stat fails #12338](https://github.com/uutils/coreutils/pull/12338) | Open |
| [gleam-lang/gleam](https://github.com/gleam-lang/gleam) | [remove: don't fail when manifest.toml is missing #5721](https://github.com/gleam-lang/gleam/pull/5721) | Merged |
| [gleam-lang/gleam](https://github.com/gleam-lang/gleam) | [Simplify the failed Hex API key decryption error message #5741](https://github.com/gleam-lang/gleam/pull/5741) | Open |
| [gleam-lang/gleam](https://github.com/gleam-lang/gleam) | [Show a readable error when reverting a release that's too old #5742](https://github.com/gleam-lang/gleam/pull/5742) | Open |
| [cross-rs/cross](https://github.com/cross-rs/cross) | [shared: point users at cargo and cross-toolchains in no-image error #1775](https://github.com/cross-rs/cross/pull/1775) | Open |
| [uutils/coreutils](https://github.com/uutils/coreutils) | [nohup: create nohup.out with mode 0600 #12339](https://github.com/uutils/coreutils/pull/12339) | Merged |
| [uutils/coreutils](https://github.com/uutils/coreutils) | [dd: don't silently swallow truncate failures #12340](https://github.com/uutils/coreutils/pull/12340) | Open |
| [uutils/coreutils](https://github.com/uutils/coreutils) | [id: don't exit 1 when uid/gid name lookup fails in default output #12341](https://github.com/uutils/coreutils/pull/12341) | Open |
| [livekit/rust-sdks](https://github.com/livekit/rust-sdks) | [webrtc-sys: don't panic when C++ hands us a malformed RtcError string #1098](https://github.com/livekit/rust-sdks/pull/1098) | Open |
| [jj-vcs/jj](https://github.com/jj-vcs/jj) | [templates: expose builtin_workspace_list alias #9518](https://github.com/jj-vcs/jj/pull/9518) | Open |
| [BurntSushi/walkdir](https://github.com/BurntSushi/walkdir) | [include parent directory path on mid-iteration errors #211](https://github.com/BurntSushi/walkdir/pull/211) | Open |
| [risingwavelabs/risingwave](https://github.com/risingwavelabs/risingwave) | [test(interval): cover mid-string +/- separators #25676](https://github.com/risingwavelabs/risingwave/pull/25676) | Open |
| [jbeder/yaml-cpp](https://github.com/jbeder/yaml-cpp) | [emit secondary tag handles (e.g. !!str) on Node::SetTag #1437](https://github.com/jbeder/yaml-cpp/pull/1437) | Open |
| [quickwit-oss/tantivy](https://github.com/quickwit-oss/tantivy) | [postings: add a basic test for TermFrequencyRecorder #2934](https://github.com/quickwit-oss/tantivy/pull/2934) | Open |
| [BurntSushi/fst](https://github.com/BurntSushi/fst) | [docs: fix memmap2 link and drop unused Streamer import #180](https://github.com/BurntSushi/fst/pull/180) | Open |
| [datamade/usaddress](https://github.com/datamade/usaddress) | [stub: add RepeatedLabelError to \_\_init\_\_.pyi #408](https://github.com/datamade/usaddress/pull/408) | Open |
| [openstates/openstates-core](https://github.com/openstates/openstates-core) | [Validate event document URLs as URIs #192](https://github.com/openstates/openstates-core/pull/192) | Open |
| [openstates/openstates-scrapers](https://github.com/openstates/openstates-scrapers) | [Default the action categorizer Rule to case-insensitive matching #5672](https://github.com/openstates/openstates-scrapers/pull/5672) | Open |
| [openstates/openstates-scrapers](https://github.com/openstates/openstates-scrapers) | [Drop redundant (?i) prefixes from utils.actions.Rule patterns #5673](https://github.com/openstates/openstates-scrapers/pull/5673) | Open |
| [openstates/openstates-scrapers](https://github.com/openstates/openstates-scrapers) | [utils.actions: import Iterable from collections.abc #5674](https://github.com/openstates/openstates-scrapers/pull/5674) | Merged |
| [mysociety/mapit](https://github.com/mysociety/mapit) | [Return JSON for 404s, matching the rest of the API #444](https://github.com/mysociety/mapit/pull/444) | Open |
| [mysociety/mapit](https://github.com/mysociety/mapit) | [Surface decode errors when reading feature names during import #445](https://github.com/mysociety/mapit/pull/445) | Open |
| [mysociety/fixmystreet](https://github.com/mysociety/fixmystreet) | [FAQ: point downtime guidance at the status page, not Twitter #5979](https://github.com/mysociety/fixmystreet/pull/5979) | Merged |
| [MobilityData/awesome-transit](https://github.com/MobilityData/awesome-transit) | [Update Dede entry; mark Instabus as no longer maintained #371](https://github.com/MobilityData/awesome-transit/pull/371) | Open |
| [simonw/datasette](https://github.com/simonw/datasette) | [docs: mention WAL mode for concurrently written databases #2718](https://github.com/simonw/datasette/pull/2718) | Open |
| [simonw/json-flatten](https://github.com/simonw/json-flatten) | [Fix unflatten crashing on keys that contain a dollar sign #11](https://github.com/simonw/json-flatten/pull/11) | Open |
| [simonw/symbex](https://github.com/simonw/symbex) | [Render dotted base classes and metaclass values instead of dropping them #49](https://github.com/simonw/symbex/pull/49) | Open |
| [huggingface/accelerate](https://github.com/huggingface/accelerate) | [logging: stop warning_once from crashing on unhashable kwargs like extra={...} #4047](https://github.com/huggingface/accelerate/pull/4047) | Open |
| [huggingface/tokenizers](https://github.com/huggingface/tokenizers) | [Fix typo in EncodingVisualizer.annotation_converter attribute #2068](https://github.com/huggingface/tokenizers/pull/2068) | Open |
| [huggingface/peft](https://github.com/huggingface/peft) | [Return False from is_gptqmodel_available when gptqmodel isn't installed #3255](https://github.com/huggingface/peft/pull/3255) | Open |
| [18F/charlie](https://github.com/18F/charlie) | [tau-bot: skip times the author marked as local #602](https://github.com/18F/charlie/pull/602) | Merged |
| [18F/charlie](https://github.com/18F/charlie) | [InclusionBot: move religious-tradition entries from Racist to Other #603](https://github.com/18F/charlie/pull/603) | Open |
| [codeforboston/maple](https://github.com/codeforboston/maple) | [Remove showLLMFeatures feature flag #2142](https://github.com/codeforboston/maple/pull/2142) | Open |
| [bloom-housing/bloom](https://github.com/bloom-housing/bloom) | [listing: skip amiChart findMany when no units carry an AMI chart #6316](https://github.com/bloom-housing/bloom/pull/6316) | Open |
| [nycdb/nycdb](https://github.com/nycdb/nycdb) | [docs: cover scripts/test and create_dataset.py in the new-dataset guide #401](https://github.com/nycdb/nycdb/pull/401) | Open |
| [DemocracyClub/WhoCanIVoteFor](https://github.com/DemocracyClub/WhoCanIVoteFor) | [Strip query strings when extracting Facebook/Instagram usernames #2392](https://github.com/DemocracyClub/WhoCanIVoteFor/pull/2392) | Open |
| [DemocracyClub/yournextrepresentative](https://github.com/DemocracyClub/yournextrepresentative) | [Allow 18-year-olds to enter their birth year #2752](https://github.com/DemocracyClub/yournextrepresentative/pull/2752) | Open |
| [DemocracyClub/yournextrepresentative](https://github.com/DemocracyClub/yournextrepresentative) | [Strip mailto: prefix from email identifiers #2753](https://github.com/DemocracyClub/yournextrepresentative/pull/2753) | Open |
| [DemocracyClub/yournextrepresentative](https://github.com/DemocracyClub/yournextrepresentative) | [Shuffle the open duplicate-suggestion list #2754](https://github.com/DemocracyClub/yournextrepresentative/pull/2754) | Open |
| [openelections/openelections-core](https://github.com/openelections/openelections-core) | [bake: tell the user when there's nothing to bake #293](https://github.com/openelections/openelections-core/pull/293) | Merged |
| [mysociety/theyworkforyou](https://github.com/mysociety/theyworkforyou) | [Use Plaid Cymru's green for the party dot #2017](https://github.com/mysociety/theyworkforyou/pull/2017) | Merged |
| [mysociety/alaveteli](https://github.com/mysociety/alaveteli) | [Stop relying on contributor order in update_contributors spec #9258](https://github.com/mysociety/alaveteli/pull/9258) | Open |
| [BlinkTagInc/gtfs-to-html](https://github.com/BlinkTagInc/gtfs-to-html) | [Pin pbf to v3 to fix the missing dist/pbf.js error #199](https://github.com/BlinkTagInc/gtfs-to-html/pull/199) | Open |
| [mysociety/mysoc-validator](https://github.com/mysociety/mysoc-validator) | [Don't choke on duplicate identifier rows in from_identifier #15](https://github.com/mysociety/mysoc-validator/pull/15) | Open |
| [mysociety/theyworkforyou](https://github.com/mysociety/theyworkforyou) | [Fix 'seperate' typos in two comments #2018](https://github.com/mysociety/theyworkforyou/pull/2018) | Merged |
| [DemocracyClub/WhoCanIVoteFor](https://github.com/DemocracyClub/WhoCanIVoteFor) | [Clear emblem_url when a party drops its emblem upstream #2393](https://github.com/DemocracyClub/WhoCanIVoteFor/pull/2393) | Open |
| [nycdb/nycdb](https://github.com/nycdb/nycdb) | [src/README: correct Python and Postgres minimums #402](https://github.com/nycdb/nycdb/pull/402) | Open |
| [codeforboston/maple](https://github.com/codeforboston/maple) | [Send logged-out users to login when clicking Follow #2143](https://github.com/codeforboston/maple/pull/2143) | Open |
| [openstates/pyopenstates](https://github.com/openstates/pyopenstates) | [Sync legislator/district docstrings with actual signatures #28](https://github.com/openstates/pyopenstates/pull/28) | Open |
| [mysociety/alaveteli](https://github.com/mysociety/alaveteli) | [Move setSelect into the Jcrop init callback on the photo crop page #9259](https://github.com/mysociety/alaveteli/pull/9259) | Open |
| [DemocracyClub/yournextrepresentative](https://github.com/DemocracyClub/yournextrepresentative) | [Fix 'seperate' / 'moemnt' typos in comments and docs #2755](https://github.com/DemocracyClub/yournextrepresentative/pull/2755) | Open |
| [mysociety/fixmystreet](https://github.com/mysociety/fixmystreet) | [Fix a few comment/doc typos #5980](https://github.com/mysociety/fixmystreet/pull/5980) | Merged |
| [DemocracyClub/WhoCanIVoteFor](https://github.com/DemocracyClub/WhoCanIVoteFor) | [Fix 'Idenfitier' and 'psuedo' typos on Party.ec_id #2394](https://github.com/DemocracyClub/WhoCanIVoteFor/pull/2394) | Open |
| [mysociety/fixmystreet](https://github.com/mysociety/fixmystreet) | [Don't redirect inspector form back to /report/update referer #5981](https://github.com/mysociety/fixmystreet/pull/5981) | Open |
| [mysociety/alaveteli](https://github.com/mysociety/alaveteli) | [Mask attachment HTML text nodes only, not href/src attributes #9260](https://github.com/mysociety/alaveteli/pull/9260) | Open |
| [DemocracyClub/yournextrepresentative](https://github.com/DemocracyClub/yournextrepresentative) | [Reject adding a person to two ballots from the same election #2756](https://github.com/DemocracyClub/yournextrepresentative/pull/2756) | Open |
| [openstates/openstates.org](https://github.com/openstates/openstates.org) | [Validate lat/lon as floats before interpolating into the geo GraphQL query #463](https://github.com/openstates/openstates.org/pull/463) | Open |
| [DemocracyClub/WhoCanIVoteFor](https://github.com/DemocracyClub/WhoCanIVoteFor) | [Sweep up stale wikipedia_bio rows in the daily import #2395](https://github.com/DemocracyClub/WhoCanIVoteFor/pull/2395) | Open |
| [openstates/openstates-core](https://github.com/openstates/openstates-core) | [Stop using deprecated datetime.utcnow() #193](https://github.com/openstates/openstates-core/pull/193) | Open |
| [mysociety/alaveteli](https://github.com/mysociety/alaveteli) | [Pick up replacement file's content_type before regenerating filename #9261](https://github.com/mysociety/alaveteli/pull/9261) | Open |
| [DemocracyClub/yournextrepresentative](https://github.com/DemocracyClub/yournextrepresentative) | [Skip diff_html for photo actions #2757](https://github.com/DemocracyClub/yournextrepresentative/pull/2757) | Open |
| [nycdb/nycdb](https://github.com/nycdb/nycdb) | [List sql/data subdirectories in packages to silence build warnings #403](https://github.com/nycdb/nycdb/pull/403) | Open |
| [CodeForPhilly/philly-ward-leaders](https://github.com/CodeForPhilly/philly-ward-leaders) | [Shrink font further on long ward-leader names #357](https://github.com/CodeForPhilly/philly-ward-leaders/pull/357) | Open |
| [datamade/census](https://github.com/datamade/census) | [Switch ACS/SF1/PL endpoints on fields() too #168](https://github.com/datamade/census/pull/168) | Open |
| [datamade/census](https://github.com/datamade/census) | [ACS5: restrict state_county_blockgroup to 2013+ #169](https://github.com/datamade/census/pull/169) | Open |
| [datamade/django-councilmatic](https://github.com/datamade/django-councilmatic) | [Escape Solr-special chars and colons in RSS facet values #295](https://github.com/datamade/django-councilmatic/pull/295) | Open |
| [datamade/parserator](https://github.com/datamade/parserator) | [docs: fix represention typo #55](https://github.com/datamade/parserator/pull/55) | Open |
| [datamade/parserator](https://github.com/datamade/parserator) | [Skip XML comments and empty sequences in TrainingData iteration #56](https://github.com/datamade/parserator/pull/56) | Open |
| [datamade/searchable-map-template-csv](https://github.com/datamade/searchable-map-template-csv) | [Skip CSV rows with empty or non-numeric lat/lng #33](https://github.com/datamade/searchable-map-template-csv/pull/33) | Open |
| [datamade/cookiecutter-django-app](https://github.com/datamade/cookiecutter-django-app) | [Make flake8 pre-commit exclude a proper regex #15](https://github.com/datamade/cookiecutter-django-app/pull/15) | Open |
| [datamade/chi-councilmatic](https://github.com/datamade/chi-councilmatic) | [get_legistar_link: rewrite stale chicago.legistar.com URLs to eLMS #430](https://github.com/datamade/chi-councilmatic/pull/430) | Open |
| [gobuffalo/fizz](https://github.com/gobuffalo/fizz) | [translators/postgres: respect null: false in change_column #144](https://github.com/gobuffalo/fizz/pull/144) | Open |
| [schollz/croc](https://github.com/schollz/croc) | [Dockerfile: bump builder image to golang:1.25 #1108](https://github.com/schollz/croc/pull/1108) | Merged |
| [SchemaStore/schemastore](https://github.com/SchemaStore/schemastore) | [claude-code-settings: add MultiEdit to permission rule regex #5701](https://github.com/SchemaStore/schemastore/pull/5701) | Open |
| [cosmos/cosmos-sdk](https://github.com/cosmos/cosmos-sdk) | [types/query: saturate Paginate end when offset+limit overflows #26430](https://github.com/cosmos/cosmos-sdk/pull/26430) | Open |
| [elastic/beats](https://github.com/elastic/beats) | [filebeat: nil-check UDP RemoteAddr before formatting in debug log #50770](https://github.com/elastic/beats/pull/50770) | Merged |
| [gorilla/securecookie](https://github.com/gorilla/securecookie) | [Add SecureCookie.Err for surfacing deferred configuration errors #92](https://github.com/gorilla/securecookie/pull/92) | Open |
| [google/go-jsonnet](https://github.com/google/go-jsonnet) | [parseYaml: drop the stray null when the stream starts with comments #875](https://github.com/google/go-jsonnet/pull/875) | Open |
| [influxdata/influxdb-client-go](https://github.com/influxdata/influxdb-client-go) | [write/service: handle a nil URL from url.Parse without panicking #427](https://github.com/influxdata/influxdb-client-go/pull/427) | Open |
| [asaskevich/govalidator](https://github.com/asaskevich/govalidator) | [Accept domain labels with multiple consecutive hyphens in IsURL #513](https://github.com/asaskevich/govalidator/pull/513) | Open |
| [exoscale/terraform-provider-exoscale](https://github.com/exoscale/terraform-provider-exoscale) | [instance: don't panic reading an instance destroyed out-of-band #536](https://github.com/exoscale/terraform-provider-exoscale/pull/536) | Open |
| [quinn-rs/quinn](https://github.com/quinn-rs/quinn) | [streams: reject STOP_SENDING and MAX_STREAM_DATA beyond the stream limit #2652](https://github.com/quinn-rs/quinn/pull/2652) | Open |

| [alecthomas/kong](https://github.com/alecthomas/kong) | [Support the env tag on positional arguments (closes #556) #601](https://github.com/alecthomas/kong/pull/601) | Merged |
| [coredns/coredns](https://github.com/coredns/coredns) | [plugin/file: canonicalize escape form in owner names #8109](https://github.com/coredns/coredns/pull/8109) | Merged |
| [freelawproject/courts-db](https://github.com/freelawproject/courts-db) | [Fix 'Washignton' typo in courts.json locations #134](https://github.com/freelawproject/courts-db/pull/134) | Merged |
| [go-sql-driver/mysql](https://github.com/go-sql-driver/mysql) | [dsn: default Net to tcp in NewConfig so Addr-only configs round-trip #1770](https://github.com/go-sql-driver/mysql/pull/1770) | Merged |
| [openelections/openelections-core](https://github.com/openelections/openelections-core) | [Narrow bare excepts in id/oh datasources #296](https://github.com/openelections/openelections-core/pull/296) | Merged |
| [openelections/openelections-data-co](https://github.com/openelections/openelections-data-co) | [clarity_parser: narrow bare except to Exception #72](https://github.com/openelections/openelections-data-co/pull/72) | Merged |
| [openelections/openelections-data-nh](https://github.com/openelections/openelections-data-nh) | [Narrow bare excepts to Exception in the 2012 NH scrapers #38](https://github.com/openelections/openelections-data-nh/pull/38) | Merged |
| [openelections/openelections-data-pa](https://github.com/openelections/openelections-data-pa) | [readme: update year range from 2000-2012 to 2000 onward #171](https://github.com/openelections/openelections-data-pa/pull/171) | Merged |
| [openelections/openelections-data-pa](https://github.com/openelections/openelections-data-pa) | [clarity_parser: narrow bare excepts to Exception #172](https://github.com/openelections/openelections-data-pa/pull/172) | Merged |
| [openelections/openelections-data-wi](https://github.com/openelections/openelections-data-wi) | [Drop dead Travis badge from README #75](https://github.com/openelections/openelections-data-wi/pull/75) | Merged |
| [openstates/openstates-scrapers](https://github.com/openstates/openstates-scrapers) | [nh: drop deprecated datetime.utcnow() in get_session_list #5675](https://github.com/openstates/openstates-scrapers/pull/5675) | Merged |
| [openstates/openstates-scrapers](https://github.com/openstates/openstates-scrapers) | [utils.actions: drop six.string_types in favour of str #5676](https://github.com/openstates/openstates-scrapers/pull/5676) | Merged |
| [svix/svix-webhooks](https://github.com/svix/svix-webhooks) | [csharp: use Random.Shared for svix-req-id #2335](https://github.com/svix/svix-webhooks/pull/2335) | Merged |
| [bloomberg/pystack](https://github.com/bloomberg/pystack) | [conftest: exit with a clear message when ptrace_scope blocks the test suite #309](https://github.com/bloomberg/pystack/pull/309) | Merged |
| [tobymao/sqlglot](https://github.com/tobymao/sqlglot) | [Raise ParseError, not IndexError, on an unclosed JSONPath filter #7665](https://github.com/tobymao/sqlglot/pull/7665) | Merged |
| [segmentio/encoding](https://github.com/segmentio/encoding) | [json: return writer errors from Encoder.Encode #163](https://github.com/segmentio/encoding/pull/163) | Open |
| [vektah/gqlparser](https://github.com/vektah/gqlparser) | [lexer: render invalid-character codepoint as hex, not decimal #431](https://github.com/vektah/gqlparser/pull/431) | Open |
| [eko/gocache](https://github.com/eko/gocache) | [cache(chain): return an error from Get when no caches are configured #309](https://github.com/eko/gocache/pull/309) | Open |
| [buger/jsonparser](https://github.com/buger/jsonparser) | [fix: don't panic on empty key when path enters an array #284](https://github.com/buger/jsonparser/pull/284) | Open |
| [rivo/tview](https://github.com/rivo/tview) | [table: stop InputHandler hanging when every cell is non-selectable #1155](https://github.com/rivo/tview/pull/1155) | Open |
| [spf13/pflag](https://github.com/spf13/pflag) | [ip: stop GetIP erroring when the IP flag has a nil default #478](https://github.com/spf13/pflag/pull/478) | Open |
| [cucumber/godog](https://github.com/cucumber/godog) | [suite: recover from panics in after-step and after-scenario hooks #745](https://github.com/cucumber/godog/pull/745) | Open |
| [shopspring/decimal](https://github.com/shopspring/decimal) | [fix: NumDigits underreports for some exact powers of ten #425](https://github.com/shopspring/decimal/pull/425) | Open |
| [a-h/templ](https://github.com/a-h/templ) | [examples/suspense: buffer the slot channel so producers can't leak #1401](https://github.com/a-h/templ/pull/1401) | Open |
| [go-resty/resty](https://github.com/go-resty/resty) | [fix: separate URL from -F/-d in buildCurlCmd output #1165](https://github.com/go-resty/resty/pull/1165) | Open |
| [OriginFinancial/origin-backend-take-home-assignment](https://github.com/c-tonneslan/origin-backend-take-home-assignment) | Solution (forked, public completion) — Go user-access-management service with signup + streaming-CSV eligibility endpoint | Solution |
</details>

## Projects

**[fourth-down-audit](https://github.com/c-tonneslan/fourth-down-audit)** — NFL 4th-down decision audit. Trained a new XGBoost win-probability model on 300k plays of nflverse pbp; held out 2024 and landed at log-loss 0.465, within 0.3% of nflfastR's bundled WP model on the same plays. Added a conversion logit, an FG-make logit, and an empirical punt-net lookup, then scored every 4th down in 2018-2024 with 1,500-iter bootstrap CIs per coach-season. The dashboard ranks coaches by WP lost with confidence-interval bars, filters by situation (red zone, two-minute, own territory, FG range) and decision type, and on click pops a play drawer with the three-option E[WP] breakdown and an animated WP curve over the surrounding plays. The README is explicit about what the model doesn't see (opponent strength, weather, personnel). Python pipeline + DuckDB locally, fully static Next.js export on Vercel. [Live](https://fourth-down-audit.vercel.app).

**[civic-philly](https://github.com/c-tonneslan/civic-philly)** — A real-asset civic tool, not a portfolio data-viz. 5,000+ housing developments, zoning permits, transit projects, and capital infrastructure investments in Philadelphia, joined against 408 ACS census tracts, 10 council district polygons, 239 Registered Community Organizations, every city council member's contact info, **4,212 OPA property owners** (the shell-LLC pattern catcher), and 6,400+ L&I displacement signals (demolition permits + housing-code violations). Postgres `tsvector` full-text search. Top-applicants and top-owners leaderboards. Per-district briefing pages with year-by-year activity charts. Status-history accountability tracker for stalled projects. `/this-week` content homepage. Mobile bottom-sheet UI. Per-district RSS feeds for journalists. Dynamic next/og preview cards on every project and district. Sitemap.xml so project pages are Google-indexable. `/embed` iframe, public JSON API at `/api/v1`, CSV export, methodology page, weekly per-district email digests via Resend. Built for council aides, organizers, and reporters. Next.js 16 / MapLibre GL / PostGIS on Supabase. [Live](https://civic-philly.vercel.app).

**[playcaller](https://github.com/c-tonneslan/playcaller)** — Full-stack NFL 4th down decision audit. Python pipeline trains three models (XGBoost win probability + 4th-down conversion, logistic FG make probability) on six seasons of nflfastR play-by-play and scores every 4th-down call against an analytical optimum. The Next.js dashboard ranks coaches by WP left on the field, lets you filter by season, drops you into a coach-season detail page with every play sorted by WP cost, and pops a modal play viewer with a WP bar chart for the go/punt/FG options. Headline: coaches and the model agreed about 30% of the time, and coaches punted on 9,000+ plays the model says they should have gone for. The leaderboard tracks reputational reality (Dan Campbell, Doug Pederson at the top; Pete Carroll, Vrabel at the bottom). [Live](https://playcaller-mu.vercel.app).

**[nflwin](https://github.com/c-tonneslan/nflwin)** — NFL in-game win probability model on 225k plays from six seasons of nflfastR. duckdb pulls the modeling table out of 580 MB of CSVs in under a minute; XGBoost on the standard game-state features hits log loss 0.485 and AUC 0.841 on the held-out 2023 season. Charts include calibration vs a score-only baseline, feature importance (score_diff carries 67% of the gain), a WP-vs-margin grid broken out by quarter, and a play-by-play replay of Super Bowl LVIII. Python.

**[xba-statcast](https://github.com/c-tonneslan/xba-statcast)** — Expected batting average from Statcast batted-ball physics. Same idea as Baseball Savant's xBA, trained from scratch on 230k balls in play. Four features (launch speed, launch angle, spray angle, batter side) get to AUC 0.904 with XGBoost. Per-batter xBA leaderboards flag Stanton as the unluckiest hitter in the test season (his hardest hits get tracked down because he runs like a tank). Python.

**[hoopvision](https://github.com/c-tonneslan/hoopvision)** — NBA shot quality model on three seasons of pbp (672k field goal attempts). XGBoost on court coordinates and shot-type buckets hits AUC 0.683. The first version of this got 0.89, which was suspicious; turned out is_three was derived from score_value, which is zero on every miss. The leak fix dropped AUC to a realistic 0.68 and tests/test_no_score_value_leak.py guards it. Court xFG% heatmap is the headline chart. Python.

**[bracketology](https://github.com/c-tonneslan/bracketology)** — College basketball game predictor with a Monte Carlo bracket simulator. Aggregates five seasons of ESPN team-box data into team-season efficiency stats (Dean Oliver possessions), trains on game-level diff features, lands at AUC 0.65 on 233 held-out 2023-24 tournament games. The simulator takes any 16/32/64-team list and reports each team's probability of reaching each round across 10k random tournaments. The model overrates 80-95% favorites by 10-15 points (March Madness regression to the mean is real). Python.

**[airwaves](https://github.com/c-tonneslan/airwaves)** — Tune into ~5,000 internet radio stations from a spinning 3D globe. Next.js + Three.js (via globe.gl) with country outlines, a day/night terminator that updates live, hex-bin heatmap mode, and altitude-gated city labels. NTS and KEXP get a live "on air" panel with the current show, host, and recent tracks; a TF-IDF tag index powers a "similar stations" tab; and a 2.2 MB precomputed embedding blob + transformers.js MiniLM running locally in the browser gives a "vibe search" you can type natural language into. Streams playback is a plain `<audio>` (CORS-friendly), and a tiny edge function proxies ICY metadata so the player shows the actual song title. [Live](https://airwaves-steel.vercel.app).

**[fretwise](https://github.com/c-tonneslan/fretwise)** — Interactive fretboard editor for guitar and bass with 40+ scales, modes, arpeggios, and bebop scales. Every note plays through a Karplus-Strong plucked-string synth I wrote in ~100 lines: white-noise seed into a one-zero lowpass with frequency-aware decay. No samples, no Tone.js. URL-shareable state and 10 tunings. TypeScript / Web Audio API. [Live](https://fretwise-neon.vercel.app).

**[littledb](https://github.com/c-tonneslan/littledb)** — Tiny embedded KV store in Go (~1,500 LOC) with the same family of designs as LMDB and BoltDB: 4 KB pages, alternating two-meta-page commits for crash safety, copy-on-write B+tree, freelist with pending-release tracking so readers never see torn writes. Benchmarks within 5% of bbolt on writes (both bottleneck on fsync), ~6x slower on point reads because there's deliberately no mmap.

**[pr-pulse](https://github.com/c-tonneslan/pr-pulse)** — Data analysis on 4,750 pull requests from 24 popular OSS repos. Pulled via GraphQL, loaded into DuckDB, charted with Matplotlib. Surprising headline: author association is the entire signal. Org members merge at 87%, prior contributors at 69%, drive-by strangers at 2%. PR size barely matters until you hit 1,000+ lines. Python.

**[tcppulse](https://github.com/c-tonneslan/tcppulse)** — Multi-target TCP latency monitor with a live TUI. Probes hosts in parallel via async Tokio, draws sparklines per target, reports p50/p90/p99 + loss rate. ~400 lines of Rust across four files (CLI, async probes, metrics, TUI). Tokio + Ratatui, no unsafe.

**[flamectl](https://github.com/c-tonneslan/flamectl)** — Renders a pprof profile as a single-file interactive SVG flamegraph. Takes input from a file, an HTTP URL, or stdin; emits one SVG you can attach to an issue or open in any browser. ~600 lines of Go with hand-rolled tree aggregation and SVG layout. Colors are an FNV hash of the function name so the same function stays the same color across runs.

**[agent-eval](https://github.com/c-tonneslan/agent-eval)** — From-scratch LLM agent evaluation framework. Rolls a bare ReAct loop with the Anthropic SDK (no LangChain), runs 21 tasks across web browsing, code debugging, and multi-step tool use, and scores with a mix of exact match, code test execution, and LLM-as-judge. Includes trajectory logging, failure mode classification, an HTML dashboard, and a calibration tool that computes Pearson r between judge and human scores. TypeScript.

## Links

- [c-tonneslan-portfolio.vercel.app](https://c-tonneslan-portfolio.vercel.app)
- cst0520@gmail.com

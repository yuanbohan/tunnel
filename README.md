# tunnel

`tunnel` launches a local command (such as `claude` or `codex`) and connects its session to a remote relay so you can attach from elsewhere.

## Install

Install the latest release:

```sh
curl -fsSL https://raw.githubusercontent.com/yuanbohan/tunnel/main/install.sh | sh
```

Install a specific version:

```sh
curl -fsSL https://raw.githubusercontent.com/yuanbohan/tunnel/main/install.sh | VERSION=v0.1.3 sh
```

The installer writes `tunnel` to `~/.local/bin/tunnel`. Add that directory to your `PATH` if it isn't already.

Supported targets:

- macOS Apple Silicon (`darwin/arm64`)
- macOS Intel (`darwin/amd64`)
- Linux x86_64 (`linux/amd64`)
- Linux ARM64 (`linux/arm64`)

Verify the installed version:

```sh
tunnel --version
```

## Quick start

Sign in once, then wrap any launcher you already use:

```sh
tunnel auth login
tunnel run claude
tunnel run -l api-fix codex --profile prod
```

Anything after the launcher name is forwarded to it unchanged.

## Commands

### `tunnel auth`

Manage the local agent token used by `tunnel run`.

```sh
tunnel auth login [--base-url url]   # sign in and save a token
tunnel auth logout                   # remove the saved login
tunnel auth status                   # print auth source status as JSON
```

### `tunnel run`

Launch a local command and connect it to the relay.

```sh
tunnel run [-l label] [--base-url url] [-v] <command> [args...]
```

- `-l, --label` — optional session label shown to relay clients.
- `-v, --verbose` — print relay connection status on successful startup.
- `--base-url` — relay base URL. Falls back to `TUNNEL_BASE_URL`, then `https://diaro.me`.
- `<command>` is resolved from `PATH`; remaining args pass through untouched.

### `tunnel update` / `tunnel rollback`

```sh
tunnel update     # update to the latest official release
tunnel rollback   # roll back to the previous official release
```

Set `TUNNEL_UPDATE_DISABLED=1` to skip the automatic update check that runs before `tunnel run`.

## Environment

| Variable                  | Purpose                                                          |
| ------------------------- | ---------------------------------------------------------------- |
| `TUNNEL_AUTH_TOKEN`       | Overrides the saved login for `tunnel run`.                      |
| `TUNNEL_BASE_URL`         | Default relay base URL (default: `https://diaro.me`).            |
| `TUNNEL_UPDATE_DISABLED`  | Disable the pre-`run` automatic update check when set.           |

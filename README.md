# tunnel

Public distribution repository for the `tunnel` CLI.

This repository hosts the installer script, release metadata, and versioned release assets. It is the public download surface for `tunnel`.

## Install

Install the latest release:

```sh
curl -fsSL https://raw.githubusercontent.com/yuanbohan/tunnel/main/install.sh | sh
```

Install a specific version:

```sh
curl -fsSL https://raw.githubusercontent.com/yuanbohan/tunnel/main/install.sh | VERSION=v0.1.2 sh
```

Upgrade to the current latest release:

```sh
curl -fsSL https://raw.githubusercontent.com/yuanbohan/tunnel/main/install.sh | sh
```

The installer:

- detects the current operating system and CPU architecture
- downloads the matching archive from this repository's releases
- verifies the published SHA256 checksum
- installs `tunnel` to `~/.local/bin/tunnel`

If `~/.local/bin` is not on your `PATH`, add it before running `tunnel`.

## Verify

Check the installed version:

```sh
tunnel --version
```

## Supported Platforms

- macOS Apple Silicon (`darwin/arm64`)
- macOS Intel (`darwin/amd64`)
- Linux x86_64 (`linux/amd64`)
- Linux ARM64 (`linux/arm64`)

## Releases

- Versioned archives and checksum files are published on the [Releases](https://github.com/yuanbohan/tunnel/releases) page.
- `latest.json` points the installer at the current recommended release.
- `install.sh` is the stable installation entrypoint.

## Repository Contents

- `install.sh`: public installer script
- `latest.json`: latest release metadata consumed by the installer
- GitHub Releases: versioned archives and checksums

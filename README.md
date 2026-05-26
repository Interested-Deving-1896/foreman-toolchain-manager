[update-readmes]   Mode: rewrite — migrating to template structure...
# foreman-toolchain-manager

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/foreman-toolchain-manager)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/foreman-toolchain-manager.git
cd foreman-toolchain-manager
```

## Usage

Foreman downloads tools from GitHub or GitLab and references them by their `user/repo` name, like `Roblox/foreman`.

### Configuration File

Foreman uses [TOML](https://toml.io/en/) for its configuration file. It simply takes a single `tools` entry and an enumeration of the tools you need, which looks like this:

```toml
[tools]
rojo = { github = "rojo-rbx/rojo", version = "7.0.0" }
darklua = { gitlab = "seaofvoices/darklua", version = "0.7.0" }
```

As you may already have noticed, the tool name is located at the left side of `=` and the right side contains the information necessary to download it. For GitHub tools, use `github = "user/repo-name"` and for GitLab, use `gitlab = "user/repo-name"`.

Previously, foreman was only able to download tools from GitHub and the format used to be `source = "rojo-rbx/rojo"`. For backward compatibility, foreman still supports this format.

### Hosts (Under Construction)
foreman supports Github and Gitlab as hosts by default, but you can define your own custom hosts as well using a single `hosts` entry and an enumeration of the hosts you want to download tools from, which looks like this.

```toml
[hosts]
# default hosts
# source = {source = "https://github.com", protocol = "github"}
# github = {source = "https://github.com", protocol = "github"}
# gitlab = {source = "https://gitlab.com", protocol = "gitlab"}
artifactory = {source = "https://artifactory.com", protocol = "artifactory"}

[tools]
tool = {artifactory = "tools/tool", version = "1.1.0"}
```

foreman currently only supports github, gitlab, and artifactory as protocols.

### System Tools
To start using Foreman to manage your system's default tools, create the file `~/.foreman/foreman.toml`.

A Foreman config that lists Rojo could look like:

```toml
[tools]
rojo = { github = "rojo-rbx/rojo", version = "7.0.0" }
```

Run `foreman install` from any directory to have Foreman pick up and install the tools listed in your system's Foreman config.

Now, if you run `rojo` inside of a directory that doesn't specify its own version of Rojo, Foreman will run the most recent 0.5.x release for you!

### Project Tools
Managing a project's tools with Foreman is similar to managing system tools. Just create a `foreman.toml` file in the root of your project.

A Foreman config that lists Remodel might look like this:

```toml
[tools]
remodel = { github = "rojo-rbx/remodel", version = "0.9.1" }
```

Run `foreman install` to tell Foreman to install any new binaries from this config file.

When inside this directory, the `remodel` command will run the latest 0.6.x release of Remodel installed on your system.

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/foreman-toolchain-manager`](https://github.com/Interested-Deving-1896/foreman-toolchain-manager) and mirrored through:

```
Interested-Deving-1896/foreman-toolchain-manager  ──►  OpenOS-Project-OSP/foreman-toolchain-manager  ──►  OpenOS-Project-Ecosystem-OOC/foreman-toolchain-manager
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
[MIT](https://github.com/Interested-Deving-1896/foreman-toolchain-manager/blob/main/LICENSE.txt) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->

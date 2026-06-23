[update-readmes]   Mode: rewrite — migrating to template structure...
# foreman-toolchain-manager

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/foreman-toolchain-manager)

<!-- AI:start:what-it-does -->
This project provides a toolchain manager for Roblox development, enabling streamlined management of simple binary tools required for building and deploying Roblox projects. It is designed for developers working within the Roblox ecosystem, offering features like dependency handling and environment configuration to simplify project workflows.
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
The project is structured as a Rust workspace with two members: the main `foreman` package and the `artiaa_auth` library. The `foreman` package serves as the primary toolchain manager, while `artiaa_auth` provides authentication functionality. The architecture relies on several dependencies for command execution, logging, HTTP requests, semantic versioning, and configuration parsing. Platform-specific dependencies are included for Windows and Unix systems.

Key components interact as follows:
- The `foreman` binary orchestrates toolchain management tasks, leveraging libraries like `reqwest` for HTTP operations and `serde` for configuration handling.
- The `artiaa_auth` library is used for authentication workflows.
- Cross-platform compatibility is ensured through conditional dependencies and platform-specific logic.

Directory structure:
```plaintext
.
├── .github/             # CI/CD workflows and GitHub-specific files
├── artiaa_auth/         # Authentication library
├── resources/           # Static resources
├── scripts/             # Helper scripts
├── src/                 # Main source code for the `foreman` binary
├── tests/               # Integration and unit tests
├── Cargo.toml           # Workspace and package configuration
├── Cargo.lock           # Dependency lock file
├── README.md            # Project documentation
├── LICENSE.txt          # License information
├── CHANGELOG.md         # Release notes
└── foreman.png          # Project logo
```
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
The repository uses GitHub Actions for continuous integration and release workflows. Below are the workflows and their purposes:

- **ci.yml**: Runs on pull requests and pushes to the `main` branch. It performs the following:
  - Checks Rust code formatting using `cargo fmt`.
  - Runs Clippy for linting.
  - Executes tests with `cargo test`.
  - Builds the project for supported platforms.
  - No secrets are required.

- **openssl.sh**: A script invoked by workflows to set up OpenSSL dependencies for building the project. It ensures compatibility with the `openssl` crate when the `vendored` feature is enabled. No secrets are required.

- **release.yml**: Triggers on new GitHub releases. It builds release binaries for multiple platforms and uploads them as release assets. Requires the `GITHUB_TOKEN` secret, which is automatically provided by GitHub Actions.

All workflows are located in the `.github/workflows` directory.
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
[@LPGhatguy](https://github.com/LPGhatguy) - 28 commits  
[@ZoteTheMighty](https://github.com/ZoteTheMighty) - 19 commits  
[@afujiwara-roblox](https://github.com/afujiwara-roblox) - 16 commits  
[@oltrep](https://github.com/oltrep) - 8 commits  
[@Nicell](https://github.com/Nicell) - 4 commits  
[@matthargett](https://github.com/matthargett) - 3 commits  
[@amatosov-rbx](https://github.com/amatosov-rbx) - 2 commits  
[@JohnnyMorganz](https://github.com/JohnnyMorganz) - 2 commits  
[@cliffchapmanrbx](https://github.com/cliffchapmanrbx) - 2 commits  
[@hmallen99](https://github.com/hmallen99) - 1 commit  
[@Interested-Deving-1896](https://github.com/Interested-Deving-1896) - 1 commit  
[@OverHash](https://github.com/OverHash) - 1 commit  
[@demelianov-roblox](https://github.com/demelianov-roblox) - 1 commit  
[@jeparlefrancais](https://github.com/jeparlefrancais) - 1 commit  

*Note: This repository may be a mirror. Please refer to the upstream source for additional context.*
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

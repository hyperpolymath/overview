# Overview

Hub-and-spoke repository mirroring for multi-platform open source distribution.

## What This Does

This repository provides a GitHub Actions workflow that automatically mirrors your repositories to multiple Git hosting platforms:

- **GitLab** (gitlab.com)
- **Codeberg** (codeberg.org)
- **Bitbucket** (bitbucket.org)

When you push to the `main` or `master` branch on GitHub, the workflow automatically syncs all branches and tags to enabled mirror targets.

## Quick Start

### 1. Generate SSH Keys

For each platform you want to mirror to, generate a dedicated SSH key:

```bash
# GitLab
ssh-keygen -t ed25519 -C "github-mirror-gitlab" -f gitlab_mirror_key

# Codeberg
ssh-keygen -t ed25519 -C "github-mirror-codeberg" -f codeberg_mirror_key

# Bitbucket
ssh-keygen -t ed25519 -C "github-mirror-bitbucket" -f bitbucket_mirror_key
```

### 2. Add Public Keys to Platforms

Add each public key (`*.pub`) to the respective platform:

- **GitLab**: Settings > SSH Keys
- **Codeberg**: Settings > SSH/GPG Keys
- **Bitbucket**: Personal Settings > SSH Keys

### 3. Store Private Keys in GitHub

Add the private keys as organization secrets:

- `GITLAB_SSH_KEY`
- `CODEBERG_SSH_KEY`
- `BITBUCKET_SSH_KEY`

### 4. Enable Mirrors

Set organization or repository variables to enable each mirror:

- `GITLAB_MIRROR_ENABLED` = `true`
- `CODEBERG_MIRROR_ENABLED` = `true`
- `BITBUCKET_MIRROR_ENABLED` = `true`

### 5. Create Target Repositories

Create empty repositories with the same name on each target platform under the `hyperpolymath` namespace.

## Security

See [SECURITY.md](SECURITY.md) for:

- Vulnerability reporting
- Security measures implemented
- Configuration checklist
- SSH host key update procedures

## Architecture

```
                    ┌─────────────────┐
                    │     GitHub      │
                    │  (Hub/Primary)  │
                    └────────┬────────┘
                             │
              push to main/master
                             │
         ┌───────────────────┼───────────────────┐
         ▼                   ▼                   ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│     GitLab      │ │    Codeberg     │ │    Bitbucket    │
│    (Spoke)      │ │    (Spoke)      │ │    (Spoke)      │
└─────────────────┘ └─────────────────┘ └─────────────────┘
```

## Roadmap

See [ROADMAP.adoc](ROADMAP.adoc) for planned features and improvements.

## License

AGPL-3.0-or-later

## Contributing

Contributions are welcome! Please ensure any PRs:

1. Maintain or improve security posture
2. Keep action versions pinned to commit SHAs
3. Update documentation as needed

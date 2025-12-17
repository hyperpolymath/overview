# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| main    | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability in this project, please report it responsibly:

1. **Do NOT** open a public issue
2. Email the maintainers directly or use GitHub's private vulnerability reporting feature
3. Include:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if any)

We will acknowledge receipt within 48 hours and provide a detailed response within 7 days.

## Security Measures

This repository implements the following security practices:

### Supply Chain Security

- **Pinned Action Versions**: All GitHub Actions are pinned to specific commit SHAs, not tags
- **Minimal Permissions**: Workflow uses `permissions: read-all` to limit access
- **Conditional Execution**: Mirror jobs only run when explicitly enabled via organization variables

### SSH Security

- **Host Key Verification**: SSH known hosts are verified to prevent MITM attacks
- **Ed25519 Keys**: Modern ed25519 SSH keys are used for all platform connections
- **Secrets Management**: SSH private keys are stored in GitHub organization secrets

### Workflow Security

- **Concurrency Controls**: Prevents race conditions during parallel workflow runs
- **No Secret Logging**: Secrets are never echoed or logged
- **Isolated Jobs**: Each mirror target runs in its own isolated job

## Security Configuration Checklist

Before enabling mirroring, ensure:

- [ ] SSH keys are generated with strong algorithms (ed25519 recommended)
- [ ] Private keys are stored in organization secrets, not repository secrets
- [ ] Public keys are added to target platforms (GitLab, Codeberg, Bitbucket)
- [ ] Repository variables are set to enable only desired mirrors
- [ ] Branch protection is enabled on the main branch

## Updating SSH Host Keys

If a platform rotates their SSH host keys:

1. Verify the new fingerprint from the official source:
   - GitLab: https://docs.gitlab.com/ee/user/gitlab_com/#ssh-host-keys-fingerprints
   - Codeberg: https://docs.codeberg.org/security/ssh-fingerprint/
   - Bitbucket: https://bitbucket.org/blog/ssh-host-key-changes

2. Update the corresponding `*_HOST_KEY` environment variable in `.github/workflows/mirror.yml`

3. Create a PR with the change and reference the official announcement

## License

This security policy is part of the project licensed under AGPL-3.0-or-later.

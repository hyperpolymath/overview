# Roadmap

Project roadmap for the hub-and-spoke mirroring infrastructure.

## Current Status: v1.0

### Completed

- [x] Hub-and-spoke mirror workflow
- [x] GitLab mirror support
- [x] Codeberg mirror support
- [x] Bitbucket mirror support
- [x] Supply chain security (pinned action SHAs)
- [x] SSH host key verification (MITM protection)
- [x] Concurrency controls (race condition prevention)
- [x] Conditional mirror execution via variables
- [x] Security policy documentation
- [x] Project documentation

---

## Phase 1: Enhanced Security

### High Priority

- [ ] **Dependabot configuration** - Automated action version updates with security alerts
- [ ] **CODEOWNERS file** - Protect critical workflow files with required reviewers
- [ ] **Branch protection template** - Recommended settings for main branch
- [ ] **Secret rotation guide** - Documentation for periodic SSH key rotation

### Medium Priority

- [ ] **SBOM generation** - Software Bill of Materials for supply chain transparency
- [ ] **Signed commits enforcement** - Require GPG/SSH signed commits for workflow changes
- [ ] **Audit logging** - Track mirror operations for compliance

---

## Phase 2: Additional Platforms

### Planned Integrations

- [ ] **SourceHut** (sr.ht) - Privacy-focused Git hosting
- [ ] **Gitea instances** - Self-hosted Gitea support with configurable URLs
- [ ] **AWS CodeCommit** - Enterprise Git hosting on AWS
- [ ] **Azure DevOps** - Microsoft enterprise Git hosting

### Platform Features

- [ ] **Dynamic platform configuration** - JSON/YAML config file for platform definitions
- [ ] **Platform health checks** - Verify mirror targets are accessible before push

---

## Phase 3: Operational Improvements

### Monitoring & Alerting

- [ ] **Slack/Discord notifications** - Alert on mirror failures
- [ ] **Status badge** - Mirror status badge for README
- [ ] **Failure retry logic** - Automatic retry with exponential backoff
- [ ] **Mirror verification** - Verify refs match after successful push

### Performance

- [ ] **Parallel mirroring** - Run all mirror jobs concurrently (currently sequential)
- [ ] **Incremental sync** - Only push changed refs for faster operations
- [ ] **Mirror scheduling** - Optional cron-based mirroring in addition to push triggers

---

## Phase 4: Advanced Features

### Repository Management

- [ ] **Multi-repo support** - Single workflow to manage multiple repositories
- [ ] **Selective branch mirroring** - Choose which branches to mirror per platform
- [ ] **Tag filtering** - Include/exclude tags based on patterns
- [ ] **Protected branch sync** - Special handling for protected branches

### Automation

- [ ] **Auto-create repos** - Automatically create target repos if they don't exist
- [ ] **Repository settings sync** - Mirror description, topics, visibility
- [ ] **Issue/PR mirroring** - Bidirectional issue synchronization (experimental)

---

## Phase 5: Enterprise Features

### Compliance

- [ ] **Change management integration** - ServiceNow/Jira ticket validation
- [ ] **Approval workflows** - Require manual approval for production mirrors
- [ ] **Compliance reporting** - Generate audit reports for SOC2/ISO27001

### Scale

- [ ] **Reusable workflow** - Publish as a reusable GitHub Action
- [ ] **Organization-wide deployment** - Template for all org repositories
- [ ] **Self-service portal** - Web UI for managing mirror configurations

---

## Contributing to the Roadmap

Have a feature request? Open an issue with:

1. **Use case** - What problem does this solve?
2. **Proposed solution** - How should it work?
3. **Security considerations** - Any security implications?

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| v1.0 | 2025-12-17 | Initial release with GitLab, Codeberg, Bitbucket support |

---

*Last updated: 2025-12-17*

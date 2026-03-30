# Security Policy

> RepoWrit takes the security of your source code seriously. This document explains how we handle vulnerabilities and protect your data.

---

## Reporting a Vulnerability

If you discover a security vulnerability in RepoWrit, please report it responsibly.

**Email:** [security@repowrit.com](mailto:security@repowrit.com)

Please include:

- A description of the vulnerability
- Steps to reproduce the issue
- The potential impact
- Any suggested remediation (optional)

**Do not** open a public GitHub issue for security vulnerabilities.

### Response Timeline

| Severity | Acknowledgment | Resolution Target |
|---|---|---|
| Critical | Within 4 hours | 24 hours |
| High | Within 12 hours | 72 hours |
| Medium | Within 24 hours | 7 days |
| Low | Within 48 hours | 30 days |

We will keep you informed throughout the investigation and resolution process. Reporters who follow responsible disclosure will be credited (with permission) in our changelog.

---

## How We Protect Your Code

### Zero Data Retention

Your source code is **never stored** by RepoWrit. When a commit is pushed:

1. Our webhook receives the event metadata from GitHub.
2. We fetch the commit diff via the GitHub API using a scoped installation token.
3. The diff is sent to the Anthropic API (Claude 4.5) with zero-retention settings.
4. Claude's response is used to generate documentation or executive briefings.
5. The diff is discarded from memory. It is not written to disk, database, or cache.

The only data we persist is the AI-generated output (documentation text, briefing summaries, embeddings for semantic search) — never your source code.

### No Model Training

We use the Anthropic API with an explicit zero-retention agreement. Your code:

- Is **not** stored by Anthropic
- Is **not** used to train or fine-tune any AI model
- Is processed ephemerally in a stateless API call

### Minimal GitHub Permissions

The RepoWrit GitHub App requests only:

| Permission | Access | Purpose |
|---|---|---|
| Repository contents | **Read-only** | Fetch commit diffs for analysis |
| Pull requests | **Read & Write** | Open documentation PRs |
| Webhooks | **Read-only** | Receive push events |

We do **not** request access to:
- Repository settings or admin functions
- Secrets, environment variables, or Actions
- Organization member lists or billing
- Any repository not explicitly selected during installation

### Infrastructure

| Layer | Provider | Compliance |
|---|---|---|
| Application hosting | Vercel | SOC 2 Type II |
| Database & Auth | Supabase | SOC 2 Type II |
| AI Processing | Anthropic API | SOC 2 Type II, zero-retention |
| DNS & CDN | Vercel Edge Network | Global TLS |

All data in transit is encrypted via TLS 1.2+. Data at rest (AI-generated summaries, user preferences) is encrypted in Supabase's managed PostgreSQL.

### Authentication

RepoWrit uses GitHub OAuth for authentication. We do not store passwords. Session tokens are short-lived and scoped to the authenticated user's permitted repositories.

---

## Scope

This security policy covers:

- The RepoWrit web application at [repowrit.com](https://repowrit.com)
- The RepoWrit GitHub App
- API endpoints under `repowrit.com/api/`

Third-party services (GitHub, Anthropic, Supabase, Vercel) are covered by their own security policies.

---

## Contact

- **Security issues:** [security@repowrit.com](mailto:security@repowrit.com)
- **General support:** [support@repowrit.com](mailto:support@repowrit.com)
- **Privacy inquiries:** [privacy@repowrit.com](mailto:privacy@repowrit.com)

---

*Last updated: June 2025*

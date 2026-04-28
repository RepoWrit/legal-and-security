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

### Zero Long-Term Code Storage

Your full source code is **never persisted** by RepoWrit. When a commit is pushed:

1. Our webhook receives the event metadata from GitHub.
2. We fetch the commit diff via the GitHub API using a scoped installation token.
3. The diff is sent to the Anthropic API (Claude 4.5) with zero-retention settings, or — if you've enabled BYOK — directly to your chosen AI provider with your encrypted key.
4. The model's response is used to generate documentation, executive briefings, architecture maps, or "Ask RepoWrit" answers.
5. The diff is discarded from memory. It is not written to disk, database, or cache.

The only data we persist is the AI-generated output (documentation text, briefing summaries, architecture snapshots, embeddings for semantic search) and operational metadata (commit SHAs, sync timestamps) — never your raw source code.

### No Model Training

We use the Anthropic API with an explicit zero-retention agreement, and OpenAI (for embeddings only) under the same posture. Your code:

- Is **not** stored by Anthropic or OpenAI
- Is **not** used to train or fine-tune any AI model
- Is processed ephemerally in stateless API calls

### Bring Your Own Key (BYOK)

On the BYOK, Team, and Enterprise plans you may supply your own API key for Anthropic, OpenAI, DeepSeek, or a custom-compatible endpoint.

- **Encrypted at rest** — Keys are encrypted with AES-256-GCM before storage.
- **Never logged** — Keys are stripped from logs, error reports, and telemetry.
- **Scoped use** — Keys are used only to make calls on your behalf and are decrypted in-memory only for the duration of a single request.

### Minimal GitHub Permissions

The RepoWrit GitHub App requests only:

| Permission | Access | Purpose |
|---|---|---|
| Repository contents | **Read-only** | Fetch commit diffs for analysis |
| Pull requests | **Read & Write** | Open documentation PRs and post review comments |
| Webhooks | **Read-only** | Receive push and pull request events |
| Members (organization) | **Read-only** | Resolve role for Team / Enterprise org plans |

We do **not** request access to:
- Repository settings or admin functions
- Secrets, environment variables, or Actions
- Organization billing or owner-level admin settings
- Any repository not explicitly selected during installation

### Infrastructure

| Layer | Provider | Compliance |
|---|---|---|
| Application hosting | Vercel | SOC 2 Type II |
| Database & Auth | Supabase (Postgres + pgvector) | SOC 2 Type II |
| AI Processing | Anthropic API | SOC 2 Type II, zero-retention |
| Embeddings | OpenAI API | SOC 2 Type II |
| Email delivery | Resend | SOC 2 Type II |
| Rate limiting | Upstash Redis | SOC 2 Type II |
| Metrics | Tinybird | SOC 2 Type II |
| Error tracking | Sentry | SOC 2 Type II |
| Product analytics | PostHog (privacy-first, identified-only) | SOC 2 Type II |
| DNS & CDN | Vercel Edge Network | Global TLS |

All data in transit is encrypted via TLS 1.2+. Data at rest (AI-generated summaries, embeddings, BYOK keys, audit trails) is encrypted in Supabase's managed Postgres. BYOK API keys receive an additional application-layer AES-256-GCM envelope.

### Authentication & Access Control

- GitHub OAuth (PKCE) for authentication. We do not store passwords.
- Session tokens are short-lived and scoped to the authenticated user.
- Role-based access control on Team and Enterprise plans (Owner / Admin / Viewer).
- All admin and governance actions are written to a SHA-256 hashed, tamper-evident audit trail.

### Application Security

- CSRF protection on all state-changing endpoints.
- Strict Content Security Policy headers.
- Per-user, per-tier rate limiting via Upstash sliding-window counters.
- CSV exports are formula-prefixed to prevent CSV-injection attacks.
- Webhook signatures from GitHub and Lemon Squeezy are verified on every request.
- Continuous error monitoring via Sentry; security-relevant events are alerted in real time.

---

## Scope

This security policy covers:

- The RepoWrit web application at [repowrit.com](https://repowrit.com)
- The RepoWrit GitHub App
- API endpoints under `repowrit.com/api/`

Third-party services (GitHub, Anthropic, OpenAI, Supabase, Vercel, Resend, Upstash, Tinybird, Sentry, PostHog, Lemon Squeezy) are covered by their own security policies.

---

## Contact

- **Security issues:** [security@repowrit.com](mailto:security@repowrit.com)
- **General support & privacy inquiries:** [support@repowrit.com](mailto:support@repowrit.com)

---

*Last updated: April 2026*


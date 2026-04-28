# Privacy Policy

> **RepoWrit** · Effective April 2026
>
> The short version: We process your commit diffs to generate documentation. We don't store your source code long-term. We don't train AI models on your data. We collect the minimum information needed to run the service.

---

## What We Collect

### Information you provide

- **GitHub account details** — When you sign in via GitHub OAuth, we receive your GitHub username, email address, and avatar URL. We use this to create and manage your RepoWrit account.
- **Repository selections** — You choose which repositories to connect. We only access repositories you explicitly grant permission to.
- **Plan and billing information** — If you subscribe to a paid plan, payment is processed by Lemon Squeezy (our Merchant of Record). We store your plan tier and subscription status. We do not store credit card numbers.
- **Bring-Your-Own-Key (BYOK) credentials** — If you enable BYOK, your AI provider API keys are encrypted at rest using AES-256-GCM and used only to make calls on your behalf. They are never logged or shared.
- **Organization membership** — For Team and Enterprise plans, we store organization membership and role (Owner / Admin / Viewer) for the orgs you connect.

### Information we generate

- **AI-generated documentation** — README updates, changelog entries, and feature docs produced by Claude 4.5 from your commit diffs. These are stored so we can open pull requests and display them in your dashboard.
- **Executive briefings** — Founder, PM, and CTO view summaries generated from commit metadata and diffs. Stored for display in your dashboard and weekly email briefings.
- **Architecture maps** — AI-generated module-layer and dependency-graph snapshots derived from your code structure. Cached for 24 hours.
- **Embeddings** — Numerical vector representations (OpenAI `text-embedding-3-small`, 1536 dimensions) of commit summaries, used to power "Ask RepoWrit" semantic search. These are mathematical abstractions — they cannot be reverse-engineered into source code.
- **Sync logs** — Timestamps, commit hashes, branch names, and processing status for each analyzed commit. Used for debugging and the sync history table in your dashboard.
- **Audit trail** — For Team and Enterprise plans, tamper-evident audit records (SHA-256 hashed) covering admin actions, governance exports, and configuration changes.

### Information we do NOT collect

- **Your full source code** — Diffs are processed in-memory and discarded immediately. We never write your code to disk, database, or any persistent storage.
- **Repository secrets** — We do not access environment variables, API keys, GitHub Actions secrets, or deployment configurations.
- **Organization billing or admin settings** — We read organization membership for tier enforcement, but we do not access org billing, payment methods, or owner-only admin settings.
- **Browsing history** — We use PostHog for privacy-first product analytics (identified-users only, no cross-site tracking).

---

## How We Use Your Data

| Data | Purpose | Retention |
|---|---|---|
| GitHub profile (username, email, avatar) | Account creation and authentication | Until account deletion |
| Repository selections | Scope webhook processing and access | Until you remove the repo or uninstall the app |
| Commit diffs | Input to Claude 4.5 for documentation generation | **Not retained** — processed in-memory, discarded immediately |
| AI-generated docs, briefings, architecture maps | Display in dashboard, open PRs, send weekly briefings | Until account deletion |
| Embeddings | Power "Ask RepoWrit" semantic search | Until account deletion |
| Sync logs | Debugging, sync history display | 90 days, then deleted |
| Plan tier & subscription status | Feature gating, billing | Until account deletion |
| BYOK API keys (encrypted) | Calling your chosen AI provider on your behalf | Until you remove them |
| Audit trail (Team / Enterprise) | SOC 2 compliance and governance reporting | 12 months |
| Anonymous analytics (PostHog) | Product improvement | 12 months |
| Error telemetry (Sentry) | Reliability and incident response | 90 days |

---

## AI Processing

RepoWrit uses the **Anthropic API** (Claude 4.5) for documentation generation, executive briefings, architecture mapping, and answer synthesis in Ask RepoWrit. We use **OpenAI** (`text-embedding-3-small`) only for generating the vector embeddings that power semantic search.

- **Zero-retention API usage** — We use both providers with zero-retention settings where available. Inputs and outputs are not retained by the providers beyond the duration of the request.
- **No model training** — Your code is never used to train, fine-tune, or improve any AI model — neither ours nor any third party's.
- **Diffs only** — We send the commit diff (changes only), not your full repository. The diff is the minimum context needed to generate accurate documentation.
- **Stateless processing** — Each API call is independent. The model does not retain memory between requests.
- **BYOK** — On the BYOK, Team, and Enterprise plans you may use your own AI provider API key. In that case the request goes directly from RepoWrit to your provider with your key; we never store the model's input or output beyond what's needed to render results.

---

## Third-Party Services

| Service | Role | Their Privacy Policy |
|---|---|---|
| [GitHub](https://github.com) | Authentication, repository access, webhooks | [github.com/privacy](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement) |
| [Anthropic](https://anthropic.com) | AI processing (Claude 4.5) | [anthropic.com/privacy](https://www.anthropic.com/privacy) |
| [OpenAI](https://openai.com) | Embeddings for semantic search | [openai.com/policies/privacy-policy](https://openai.com/policies/privacy-policy) |
| [Supabase](https://supabase.com) | Database (Postgres + pgvector), authentication | [supabase.com/privacy](https://supabase.com/privacy) |
| [Vercel](https://vercel.com) | Application hosting and edge compute | [vercel.com/legal/privacy-policy](https://vercel.com/legal/privacy-policy) |
| [Lemon Squeezy](https://lemonsqueezy.com) | Merchant of Record, payment processing | [lemonsqueezy.com/privacy](https://www.lemonsqueezy.com/privacy) |
| [Resend](https://resend.com) | Transactional and weekly briefing email delivery | [resend.com/legal/privacy-policy](https://resend.com/legal/privacy-policy) |
| [Upstash](https://upstash.com) | Distributed rate limiting (Redis) | [upstash.com/trust/privacy.pdf](https://upstash.com/trust/privacy.pdf) |
| [Tinybird](https://tinybird.co) | Aggregated metrics and analytics | [tinybird.co/legal/privacy-policy](https://www.tinybird.co/legal/privacy-policy) |
| [Sentry](https://sentry.io) | Error tracking and performance monitoring | [sentry.io/privacy](https://sentry.io/privacy/) |
| [PostHog](https://posthog.com) | Privacy-first product analytics | [posthog.com/privacy](https://posthog.com/privacy) |

We do not sell, rent, or share your data with any parties beyond those listed above.

---

## Your Rights

You can exercise the following at any time:

- **Access** — View all data we hold about you in your [account settings](https://repowrit.com/account).
- **Delete** — Delete your account and all associated data by emailing [support@repowrit.com](mailto:support@repowrit.com). We will process deletion requests within 7 business days.
- **Disconnect** — Remove individual repositories from RepoWrit at any time. We will stop processing commits and delete associated sync logs within 24 hours.
- **Uninstall** — Uninstall the GitHub App entirely from your GitHub settings. This immediately revokes all access.
- **Export** — Request an export of your data by emailing [support@repowrit.com](mailto:support@repowrit.com). Team and Enterprise users can also export governance reports and audit trails directly from the dashboard.

---

## Cookies

RepoWrit uses minimal cookies. Only strictly necessary cookies are set by default; analytics cookies are gated behind the consent banner.

| Cookie | Purpose | Duration |
|---|---|---|
| Supabase auth tokens / PKCE verifier | Authentication | Session |
| Theme preference | Dark / Light / Ocean / Rosé | 1 year |
| Cookie consent | Remembers your analytics preference | 1 year |
| PostHog anonymous ID (with consent) | Product analytics | 12 months |

We do not use advertising cookies or cross-site tracking. See our full [Cookie Policy](https://repowrit.com/cookies).

---

## Children's Privacy

RepoWrit is not intended for use by anyone under 16 years of age. We do not knowingly collect information from children.

---

## Changes to This Policy

We may update this policy from time to time. Material changes will be communicated via email to registered users and posted on our [changelog](https://repowrit.com/changelog). The "Effective" date at the top of this document will be updated accordingly.

---

## Contact

- **Privacy & general inquiries:** [support@repowrit.com](mailto:support@repowrit.com)
- **Security issues:** [security@repowrit.com](mailto:security@repowrit.com)

---

*Last updated: April 2026*


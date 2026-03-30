# Privacy Policy

> **RepoWrit** · Effective June 2025
>
> The short version: We process your commit diffs to generate documentation. We don't store your source code. We don't train AI models on your data. We collect the minimum information needed to run the service.

---

## What We Collect

### Information you provide

- **GitHub account details** — When you sign in via GitHub OAuth, we receive your GitHub username, email address, and avatar URL. We use this to create and manage your RepoWrit account.
- **Repository selections** — You choose which repositories to connect. We only access repositories you explicitly grant permission to.
- **Plan and billing information** — If you subscribe to a paid plan, payment is processed by Lemon Squeezy. We store your plan tier and subscription status. We do not store credit card numbers.

### Information we generate

- **AI-generated documentation** — README updates, changelog entries, and feature docs produced by Claude 4.5 from your commit diffs. These are stored so we can open pull requests and display them in your dashboard.
- **Executive briefings** — Founder, PM, and CTO view summaries generated from commit metadata and diffs. Stored for display in your dashboard.
- **Embeddings** — Numerical vector representations of commit summaries for semantic search. These are mathematical abstractions — they cannot be reverse-engineered into source code.
- **Sync logs** — Timestamps, commit hashes, and processing status for each analyzed commit. Used for debugging and the sync history table in your dashboard.

### Information we do NOT collect

- **Your source code** — Diffs are processed in-memory and discarded immediately. We never write your code to disk, database, or any persistent storage.
- **Repository secrets** — We do not access environment variables, API keys, GitHub Actions secrets, or deployment configurations.
- **Organization member data** — We do not access your GitHub organization's member list, billing, or admin settings.
- **Browsing history** — We use PostHog for anonymous product analytics (page views, feature usage). We do not track you across other websites.

---

## How We Use Your Data

| Data | Purpose | Retention |
|---|---|---|
| GitHub profile (username, email, avatar) | Account creation and authentication | Until account deletion |
| Repository selections | Scope webhook processing and access | Until you remove the repo or uninstall the app |
| Commit diffs | Input to Claude 4.5 for documentation generation | **Not retained** — processed in-memory, discarded immediately |
| AI-generated docs & briefings | Display in dashboard, open PRs | Until account deletion |
| Embeddings | Power semantic search | Until account deletion |
| Sync logs | Debugging, sync history display | 90 days, then deleted |
| Plan tier & subscription status | Feature gating, billing | Until account deletion |
| Anonymous analytics (PostHog) | Product improvement | 12 months |

---

## AI Processing

RepoWrit uses the **Anthropic API** (Claude 4.5) to analyze commit diffs and generate documentation.

- **Zero-retention API usage** — Anthropic does not store inputs or outputs from our API calls. This is contractually guaranteed under our API agreement.
- **No model training** — Your code is never used to train, fine-tune, or improve any AI model — neither ours nor Anthropic's.
- **Diffs only** — We send the commit diff (changes only), not your full repository. The diff is the minimum context needed to generate accurate documentation.
- **Stateless processing** — Each API call is independent. Claude does not retain memory between requests.

---

## Third-Party Services

| Service | Role | Their Privacy Policy |
|---|---|---|
| [GitHub](https://github.com) | Authentication, repository access | [github.com/privacy](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement) |
| [Anthropic](https://anthropic.com) | AI processing (Claude 4.5) | [anthropic.com/privacy](https://www.anthropic.com/privacy) |
| [Supabase](https://supabase.com) | Database, authentication | [supabase.com/privacy](https://supabase.com/privacy) |
| [Vercel](https://vercel.com) | Application hosting | [vercel.com/legal/privacy-policy](https://vercel.com/legal/privacy-policy) |
| [Lemon Squeezy](https://lemonsqueezy.com) | Payment processing | [lemonsqueezy.com/privacy](https://www.lemonsqueezy.com/privacy) |
| [PostHog](https://posthog.com) | Anonymous product analytics | [posthog.com/privacy](https://posthog.com/privacy) |

We do not sell, rent, or share your data with any parties beyond those listed above.

---

## Your Rights

You can exercise the following at any time:

- **Access** — View all data we hold about you in your [account settings](https://repowrit.com/account).
- **Delete** — Delete your account and all associated data by emailing [privacy@repowrit.com](mailto:privacy@repowrit.com). We will process deletion requests within 7 business days.
- **Disconnect** — Remove individual repositories from RepoWrit at any time. We will stop processing commits and delete associated sync logs within 24 hours.
- **Uninstall** — Uninstall the GitHub App entirely from your GitHub settings. This immediately revokes all access.
- **Export** — Request an export of your data by emailing [privacy@repowrit.com](mailto:privacy@repowrit.com).

---

## Cookies

RepoWrit uses minimal cookies:

| Cookie | Purpose | Duration |
|---|---|---|
| Session token | Authentication | Session (expires on browser close) |
| Theme preference | Dark/light mode | 1 year |
| PostHog anonymous ID | Anonymous analytics | 12 months |

We do not use advertising cookies or cross-site tracking. See our full [Cookie Policy](https://repowrit.com/cookies).

---

## Children's Privacy

RepoWrit is not intended for use by anyone under 16 years of age. We do not knowingly collect information from children.

---

## Changes to This Policy

We may update this policy from time to time. Material changes will be communicated via email to registered users and posted on our [changelog](https://repowrit.com/changelog). The "Effective" date at the top of this document will be updated accordingly.

---

## Contact

- **Privacy inquiries:** [privacy@repowrit.com](mailto:privacy@repowrit.com)
- **General support:** [support@repowrit.com](mailto:support@repowrit.com)
- **Security issues:** [security@repowrit.com](mailto:security@repowrit.com)

---

*Last updated: June 2025*

# Security Policy

Fiatsend takes security seriously. We handle real money, stablecoins, and sensitive identity data — so security is foundational to everything we build.

## Reporting a Vulnerability

**Do NOT open a public GitHub issue for security vulnerabilities.**

If you discover a security vulnerability in any Fiatsend repository, please report it responsibly:

### How to report

Send an email to **security@fiatsend.com** with the following:

1. **Description** — What is the vulnerability? Which component is affected?
2. **Impact** — What could an attacker do with this? (e.g., steal funds, access user data, impersonate users)
3. **Reproduction steps** — Detailed steps to reproduce the issue
4. **Proof of concept** — Code, screenshots, or logs demonstrating the vulnerability
5. **Suggested fix** — If you have one (optional but appreciated)

### What to include

- Repository and file path affected
- SDK version or commit hash
- Your contact information for follow-up

### What NOT to do

- Do not publicly disclose the vulnerability before we've had time to fix it
- Do not exploit the vulnerability beyond what is necessary to demonstrate it
- Do not access, modify, or delete other users' data
- Do not perform denial-of-service testing on production systems

## What to Expect

| Step | Timeline |
|------|----------|
| **Acknowledgment** | Within 48 hours of your report |
| **Initial assessment** | Within 5 business days |
| **Status update** | Every 7 days until resolved |
| **Fix deployed** | Depends on severity (see below) |

### Severity and response times

| Severity | Description | Target fix time |
|----------|-------------|-----------------|
| **Critical** | Fund theft, private key exposure, authentication bypass | 24–48 hours |
| **High** | User data exposure, privilege escalation, significant financial impact | 7 days |
| **Medium** | Limited data exposure, denial of service, business logic bypass | 30 days |
| **Low** | Information disclosure with minimal impact, best practice violations | 90 days |

## Scope

The following are in scope for security reports:

- **SDK packages** — `@fiatsend/sdk`, `fiatsend-python`, `fiatsend-go`
- **Smart contracts** — All contracts in the `contracts` repo
- **API** — The Fiatsend REST API at `api.fiatsend.com`
- **Authentication** — API key handling, webhook signature verification
- **Dependencies** — Vulnerabilities in our direct dependencies that affect Fiatsend users

### Out of scope

- Social engineering attacks against Fiatsend employees
- Physical security of Fiatsend offices or infrastructure
- Denial of service via volume-based attacks
- Vulnerabilities in third-party services we integrate with (report those to the respective vendor)
- Issues that require physical access to a user's device

## Recognition

We value the security research community. Reporters of valid vulnerabilities will receive:

- Credit in our security advisories (unless you prefer to remain anonymous)
- A mention in our CHANGELOG and release notes
- Our sincere gratitude

We are working toward a formal bug bounty program. Details will be announced when available.

## Supported Versions

We provide security patches for the latest major version of each SDK. Older major versions may receive critical patches on a case-by-case basis.

| SDK | Supported versions |
|-----|-------------------|
| `@fiatsend/sdk` | Latest major |
| `fiatsend-python` | Latest major |
| `fiatsend-go` | Latest major |
| Smart contracts | All deployed versions |

## PGP Key

For encrypted communication, you can use our PGP key (available upon request at security@fiatsend.com).

---

Thank you for helping keep Fiatsend and our users safe.

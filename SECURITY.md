
# Security Policy

## Supported Versions

This repository is a template project.
Security updates apply to the latest version available on the `main` branch.

---

## 🔐 Secret Handling Policy

This project demonstrates secure secret management using 1Password in GitHub Actions.

Sensitive data must never be:

- Committed to the repository
- Included in issues
- Shared in pull requests
- Logged in workflow output

Examples of sensitive data:

- Roam email address
- Roam password
- Roam graph identifiers
- GitHub Personal Access Tokens
- 1Password Service Account tokens

---

## 🛡 Recommended Security Practices

We strongly recommend:

- Using 1Password Service Accounts for CI/CD secret injection
- Restricting vault access to the minimum required scope
- Using fine-grained GitHub Personal Access Tokens
- Rotating credentials periodically
- Avoiding long-lived static credentials

Do not hardcode secrets in workflow files.

Always use placeholder references in examples, such as:

```

op://VaultName/ItemName/field

```

---

## 🚨 Reporting a Vulnerability

If you discover a security issue in this template:

1. Do not open a public issue containing sensitive details.
2. Open a GitHub issue describing the vulnerability at a high level without exposing secrets.
3. If necessary, contact the repository owner directly via GitHub profile contact information.

Please include:

- A description of the issue
- Steps to reproduce
- Potential impact
- Suggested mitigation (if available)

We aim to respond to security reports within a reasonable timeframe.

---

## ⚠ Disclaimer

This project is not affiliated with Roam Research or 1Password.

It is an independent community template intended to demonstrate secure automation practices.

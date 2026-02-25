# Roam to GitHub Backup with 1Password

A GitHub Actions template that backs up your Roam Research graph to a GitHub repository, with credentials securely managed by 1Password.

This repository is designed as a reusable template to help Roam users create automated, secure, and maintainable backups.

---

## ✨ Features

- Automatic Roam Research backup via GitHub Actions
- Scheduled and manual trigger support
- Secure credential management using 1Password
- Markdown export support
- Fully template-based and customizable

---

## 🔐 Why Use 1Password?

Instead of storing sensitive credentials (Roam email, password, GitHub token) directly in GitHub Secrets, this template demonstrates how to:

- Store credentials inside a 1Password vault
- Use a Service Account for CI/CD access
- Inject secrets into GitHub Actions at runtime
- Avoid exposing credentials in repository settings

This improves security, auditability, and secret rotation control.

---

## 🚀 How It Works

1. GitHub Actions runs on a schedule (cron) or manual trigger.
2. The workflow retrieves secrets from 1Password.
3. The `roam2github` tool exports your Roam graph.
4. Changes are committed automatically to your backup repository.

---

## 📦 Quick Start

### 1️⃣ Create a Backup Repository

Create a separate GitHub repository where your Roam backup will be stored.

Example:

```

your-username/roam-backup

```

---

### 2️⃣ Prepare 1Password

In 1Password:

1. Create a new vault (e.g., `RoamBackup`)
2. Create an item (e.g., `RoamAccount`)
3. Add the following fields:

- `roam_email`
- `roam_password`
- `roam_graph`
- `github_pat`
- `backup_repo`

4. Create a **Service Account**
5. Grant access only to this vault
6. Copy the Service Account Token

---

### 3️⃣ Add GitHub Secret

In your GitHub repository:

Settings → Secrets and variables → Actions → New repository secret

Name:

```

OP_SERVICE_ACCOUNT_TOKEN

```

Value:

```

<your-service-account-token>
```

---

### 4️⃣ Use the Workflow

Copy the workflow file from:

```
.github/workflows/backup.yml
```

Adjust the cron schedule if needed:

```yaml
schedule:
  - cron: "30 13,21 * * *"
```

You can also trigger manually via:

Actions → Run workflow

---

## ⚙ Configuration

You may customize export formats:

```yaml
BACKUP_EDN: "false"
BACKUP_JSON: "false"
BACKUP_MARKDOWN: "true"
BACKUP_FLAT_MARKDOWN: "false"
BACKUP_MSGPACK: "false"
```

Default configuration exports Markdown format.

---

## 🔄 Recommended Security Practice

* Do not store Roam credentials in plain GitHub Secrets
* Do not commit credentials into repository files
* Use fine-grained GitHub Personal Access Tokens
* Restrict 1Password Service Account vault access

---

## 🧩 Template Usage

You can:

* Fork this repository
* Use it as a template
* Copy only the workflow files
* Integrate it into your own automation stack

This project is intentionally lightweight and minimal.

---

## 📌 Limitations

* Requires valid Roam credentials
* Does not bypass Roam authentication limitations
* Requires Node.js runtime in GitHub Actions

---

## 🤝 Contributing

Contributions are welcome.

* Open an issue for suggestions
* Submit a pull request for improvements
* Security concerns should not include real credentials

---

## 🛡 Security Policy

Never submit real credentials in issues or pull requests.

If you discover a vulnerability in the workflow or secret handling logic, please open an issue describing the problem without exposing sensitive information.

---

## 📄 License

MIT License

---

## 📣 Disclaimer

This project is not affiliated with Roam Research or 1Password.
It is an independent community template demonstrating secure backup automation.


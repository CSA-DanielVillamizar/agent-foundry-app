# Security Policy

Thanks for taking the time to look. Agency Agents writes files into developer-tool configuration directories, so security reports are welcome.

---

## Supported Versions

| Version | Supported | Status |
|---------|-----------|--------|
| `0.1.x` | Yes | Current |

> [!NOTE]
> This is a pre-1.0 project. Support windows may change as release packaging stabilizes.

---

## Reporting A Vulnerability

> [!IMPORTANT]
> Please do not open a public GitHub issue for security reports.

Email **danielvillamizara@gmail.com** with:

- A clear description of the issue
- Impact
- Steps to reproduce or proof of concept
- Version or commit tested
- Name/handle for credit, if desired

---

## Response Time

Best effort commitments:

| Timeline | Commitment |
|----------|------------|
| Within 7 days | Acknowledgement |
| Within 14 days | Initial assessment |
| Within 30 days (high/critical) | Fix or mitigation plan |

---

## Scope

### In Scope ✅

- Remote code execution in the app or IPC commands
- Arbitrary file read/write through Tauri commands
- Path traversal in install, backup, catalog, or import/export paths
- Unsafe overwrite or uninstall behavior
- Bypass of modified-file backup protections
- XSS in the webview
- Token leakage from GitHub OAuth storage or IPC
- SSRF or unexpected outbound requests
- Updater signature or artifact verification bypass
- Incorrect tool path handling that writes outside documented destinations

### Out of Scope ❌

- Vulnerabilities in third-party AI coding tools
- Malicious agent content in a user-selected catalog clone
- Vulnerabilities in macOS, Windows, Linux, WebKit, or system components
- Social-engineering attacks
- Attacks requiring an already-compromised local account
- Bugs in the upstream `agency-agents` repo that do not affect app install/write behavior

---

## Disclosure Policy

Coordinated disclosure, 90-day default. If a fix takes longer, the reporter and maintainer can agree on an extension before the embargo expires.

---

## Security Posture

The app implements multiple layers of security:

| Component | Implementation |
|-----------|-----------------|
| **IPC Typed** | Typed Tauri IPC |
| **Frontend** | No frontend arbitrary shell bridge |
| **Rendering** | Deterministic renderers for supported tools |
| **Ledger** | Local ledger records app-managed writes |
| **File Backup** | Modified installed files are backed up before destructive operations |
| **Token Storage** | GitHub token is stored in the platform keychain and is not returned to the frontend |
| **Network** | Network features are gated by settings and feature boundaries |

---

## Hall Of Fame

Reporters who have responsibly disclosed security issues:

<!-- First reporter goes here. Add as: Name (handle) - short description, fix in commit/PR link -->

*(empty - be the first)*

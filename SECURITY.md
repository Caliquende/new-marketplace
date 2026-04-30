# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| latest  | :white_check_mark: |

## Reporting a Vulnerability

1. **DO NOT** open a public GitHub issue for security vulnerabilities.
2. Report via [GitHub Security Advisory](https://github.com/Caliquende/new-marketplace/security/advisories/new).
3. Include a detailed description, steps to reproduce, and any potential impact.
4. We will acknowledge your report within 48 hours.

## Security Considerations

- **Environment Variables:** The `.env` file is gitignored. Never commit secrets or API keys.
- **Dependencies:** Monitored via Dependabot for npm and GitHub Actions vulnerabilities.
- **SAST:** CodeQL and ESLint security rules scan for vulnerabilities on every push/PR.
- **npm audit:** Automated dependency vulnerability scanning runs in CI.
- **CORS:** Server-side CORS configuration should be reviewed for production deployments.
- **Input Validation:** All user inputs should be sanitized server-side before processing.

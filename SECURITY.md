# Security Policy

## Supported Versions

We actively support the following versions of Persian Tools with security updates:

| Version | Supported          | Node.js Required |
| ------- | ------------------ | ---------------- |
| 4.x     | :white_check_mark: | >= 14.x          |
| 3.x     | :white_check_mark: | >= 12.x          |
| < 3.0   | :x:                | N/A              |

## Reporting a Vulnerability

We take the security of Persian Tools seriously. If you believe you have found a security vulnerability, please report it to us responsibly.

### How to Report

**Please DO NOT report security vulnerabilities through public GitHub issues.**

Instead, please report them via one of the following methods:

1. **Email**: Send details to [ali_4286@live.com](mailto:ali_4286@live.com) with subject line "SECURITY: [Brief Description]"
2. **GitHub Security Advisory**: Use [GitHub's private vulnerability reporting](https://github.com/persian-tools/persian-tools/security/advisories/new)

### What to Include

Please include the following information in your report:

- Type of vulnerability
- Full paths of source file(s) related to the vulnerability
- Location of the affected source code (tag/branch/commit or direct URL)
- Step-by-step instructions to reproduce the issue
- Proof-of-concept or exploit code (if possible)
- Impact of the vulnerability, including how an attacker might exploit it

### Response Timeline

- **Initial Response**: We will acknowledge receipt of your vulnerability report within 48 hours
- **Status Update**: We will provide a detailed response within 7 days, including next steps
- **Fix Timeline**: We aim to release patches for confirmed vulnerabilities within 30 days
- **Disclosure**: We will coordinate disclosure timing with you after the fix is released

### Security Update Process

1. The security team will investigate and validate the report
2. A fix will be developed and tested
3. A security advisory will be published
4. The fix will be released in a patch version
5. The vulnerability will be publicly disclosed after users have had time to update

## Security Best Practices for Users

When using Persian Tools in your projects:

1. **Keep Updated**: Always use the latest version to ensure you have security patches
2. **Dependency Audits**: Regularly run `npm audit` or `bun audit` to check for vulnerabilities
3. **Input Validation**: Always validate user input before passing it to Persian Tools functions
4. **Secure Configuration**: Follow secure coding practices in your implementation
5. **Monitor Advisories**: Watch this repository for security advisories

## Known Security Considerations

### Input Validation

Persian Tools processes user-provided strings and numbers. While we validate inputs, you should:

- Sanitize user input before processing
- Implement rate limiting for public-facing applications
- Set appropriate input length limits to prevent DoS attacks

### Regular Expression Safety

Some functions use regular expressions. We:

- Test all regex patterns for ReDoS (Regular Expression Denial of Service) vulnerabilities
- Use timeouts where appropriate
- Benchmark performance with edge cases

### Dependencies

We minimize external dependencies to reduce the attack surface:

- Only one runtime dependency: `fastest-levenshtein`
- Regular security audits of all dependencies
- Automated dependency updates via Renovate/Dependabot

## Security Tools

Our CI/CD pipeline includes:

- CodeQL analysis for code vulnerabilities
- Trivy for container and dependency scanning
- TruffleHog for secret detection
- npm/bun audit for dependency vulnerabilities
- SonarCloud for code quality and security

## Bug Bounty Program

We currently do not offer a bug bounty program, but we deeply appreciate security researchers who responsibly disclose vulnerabilities to us.

## Questions

For questions about our security policy, please contact [ali_4286@live.com](mailto:ali_4286@live.com).

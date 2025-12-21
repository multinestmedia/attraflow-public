# Security Policy

## Supported Versions

We take security seriously and actively maintain the security of AttraFlow. Currently supported versions:

| Version | Supported          |
| ------- | ------------------ |
| 0.1.x   | :white_check_mark: |
| < 0.1   | :x:                |

## Security Features

AttraFlow implements comprehensive security measures:

### Privacy-First Architecture
- **Local data storage only**: All user data stays in the browser's localStorage
- **No external transmission**: No data is sent to external servers
- **No tracking**: No analytics or tracking services
- **No authentication**: No user accounts or server-side storage

### Input Validation & Sanitization
- Form input validation with type checking and range limits
- Notes field sanitization (removes control characters, limits length)
- CSV injection prevention in data exports
- Comprehensive validation for data imports (JSON and CSV)

### XSS Protection
- Content Security Policy (CSP) headers configured
- React's automatic content escaping
- X-Frame-Options, X-Content-Type-Options, and X-XSS-Protection headers
- No use of `dangerouslySetInnerHTML` in user content areas

### HTTPS Enforcement
- Strict-Transport-Security (HSTS) headers in production
- CSP `upgrade-insecure-requests` directive
- Secure cookie policies (when applicable)

### Dependency Management
- Automated dependency scanning via GitHub Dependabot
- Weekly security updates
- Zero known vulnerabilities (as of last audit)

## Reporting a Vulnerability

If you discover a security vulnerability in AttraFlow, please report it responsibly. We appreciate your efforts to improve our security.

### How to Report

**Please DO NOT report security vulnerabilities through public GitHub issues.**

Instead, please report security vulnerabilities by:

1. **Email**: Send details to [security contact - to be added]
2. **GitHub Security Advisory**: Use GitHub's private security advisory feature
   - Go to the [Security tab](https://github.com/multinestmedia/attraflow-private/security)
   - Click "Report a vulnerability"

### What to Include

Please include as much information as possible:

- Type of vulnerability (XSS, injection, etc.)
- Steps to reproduce the issue
- Potential impact of the vulnerability
- Suggested fix (if available)
- Your contact information for follow-up

### Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Timeline**: Critical vulnerabilities within 14 days

### What to Expect

1. **Acknowledgment**: We'll confirm receipt of your report
2. **Investigation**: We'll investigate and validate the vulnerability
3. **Fix Development**: We'll develop and test a fix
4. **Disclosure**: We'll coordinate disclosure timing with you
5. **Credit**: We'll credit you in our security advisory (if desired)

## Security Best Practices for Users

While AttraFlow is designed with security in mind, users should also follow best practices:

### Data Protection
- **Backup your data**: Regularly export your data using the export feature
- **Secure your device**: Use device encryption and screen locks
- **Private browsing**: Consider using private/incognito mode for sensitive data
- **Shared devices**: Clear browser data or use export/import for data portability

### Browser Security
- **Keep browser updated**: Use the latest version of your web browser
- **Security extensions**: Consider using security-focused browser extensions
- **HTTPS only**: Always access AttraFlow via HTTPS in production

## Security Audits

We conduct regular security audits:

- **Automated scanning**: Weekly via Dependabot
- **Manual review**: Quarterly comprehensive audits
- **Pre-release checks**: Security verification before each release

### Latest Audit

- **Date**: 2024-12-20
- **Status**: ✅ All security requirements met
- **Vulnerabilities Found**: 0
- **Action Items**: None critical

See [SECURITY_AUDIT.md](./SECURITY_AUDIT.md) for the full audit checklist.

## Security-Related Configuration Files

The following files contain security configurations:

- `packages/web/vite.config.ts` - CSP and security headers for dev/preview
- `packages/web/public/staticwebapp.config.json` - Production security headers
- `packages/web/src/utils/sanitize.ts` - Input sanitization utilities
- `packages/web/src/utils/dataImport.ts` - Import validation
- `packages/web/src/utils/dataExport.ts` - Export security
- `.github/dependabot.yml` - Automated dependency scanning

## Known Limitations

### PayPal Donation Widget
- The application includes a PayPal donation widget that loads external JavaScript
- This is sandboxed via CSP and only loads from trusted PayPal domains
- No user data is shared with PayPal
- This is the only external service integration

### Browser Storage
- Data is stored in browser localStorage, which is:
  - Accessible to JavaScript on the same origin
  - Not encrypted at rest (use device encryption)
  - Cleared when browser data is cleared
  - Limited to ~5-10MB (browser dependent)

## Compliance

AttraFlow is designed with privacy regulations in mind:

- **GDPR Compliant**: No personal data collection or processing
- **CCPA Compliant**: No sale or sharing of personal information
- **HIPAA**: Not applicable (not a covered entity)
- **COPPA**: Suitable for all ages (no data collection)

## Additional Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [MDN Web Security](https://developer.mozilla.org/en-US/docs/Web/Security)
- [Content Security Policy](https://content-security-policy.com/)

## Updates to This Policy

This security policy is reviewed and updated quarterly or as needed when security practices change.

**Last Updated**: 2024-12-20  
**Next Review**: 2025-03-20

---

## Hall of Fame

We thank the following security researchers for responsibly disclosing vulnerabilities:

_No vulnerabilities reported yet._

---

If you have questions about this security policy, please open a discussion in our [GitHub Discussions](https://github.com/multinestmedia/attraflow-public/discussions).

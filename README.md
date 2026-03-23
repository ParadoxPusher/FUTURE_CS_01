# Vulnerability Assessment Report

## Cyber Security Task 1 (2026)
**By Future Interns**

---

## Overview

This repository contains a comprehensive vulnerability assessment report for the **Google Gruyere Web Application**, conducted as part of the Cyber Security Task 1 internship assignment. The assessment follows ethical guidelines with a read-only scope, focusing on passive scanning and security configuration analysis.

---

## Target Information

| Property | Value |
|----------|-------|
| **Target Name** | Google Gruyere Web Application |
| **Target URL** | https://google-gruyere.appspot.com/523736207850421785785417252011919832459 |
| **Target Host** | google-gruyere.appspot.com |
| **Assessment Date** | March 22, 2026 |
| **Assessor** | Future Interns - Cybersecurity Task 1 |
| **Scope** | Read-Only Security Assessment (Passive Scanning) |

---

## Scope & Ethics

This assessment follows strict ethical guidelines:

### Allowed
- Public-facing pages only
- Passive scanning and observation
- Header checks and configuration analysis
- Security documentation review

### NOT Allowed
- Login bypass attempts
- Active exploitation
- Brute force attacks
- Denial-of-Service (DoS)
- Any activity that could harm the website

---

## Methodology

The assessment followed industry-standard methodologies:

1. **Security Header Analysis** - Examined HTTP response headers for missing security controls
2. **Configuration Review** - Analyzed application configuration and authentication mechanisms
3. **Client-Side Analysis** - Reviewed HTML source code and JavaScript files
4. **Behavioral Analysis** - Observed application behavior during normal operations

---

## Key Findings Summary

| Severity | Count | Description |
|----------|-------|-------------|
| **Critical** | 1 | Sensitive Information Exposure in URL Parameters |
| **High** | 3 | Missing Security Headers, XSS, Insecure Password Handling |
| **Medium** | 5 | CSRF, Path Traversal, File Upload, Rate Limiting, State Manipulation |
| **Low** | 1 | Information Disclosure via Error Messages |

**Total Vulnerabilities Identified: 10**

---

## Critical Finding

### VULN-001: Sensitive Information Exposure in URL Parameters

**Severity:** CRITICAL (CVSS: 7.5)

The application transmits user passwords as URL parameters in plaintext during account creation:

```
/saveprofile?action=new&uid=testuser123&pw=TestPass123&is_author=True
```

**Impact:** Passwords exposed in browser history, server logs, proxy logs, and referrer headers.

**Remediation:** Use POST requests with form data in the request body. Never transmit passwords in URLs.

---

## Tools Used

- **Browser Developer Tools** - For header analysis and client-side inspection
- **Python** - For documentation and data analysis
- **Manual Code Review** - For security logic analysis

---

## Repository Structure

```
github_repo/
├── README.md                           # This file
├── report/
│   └── vulnerability_assessment_report.pdf  # Full assessment report
└── evidence/
    └── (Screenshots and supporting evidence)
```

---

## Report Contents

The full PDF report (16 pages) includes:

1. **Executive Summary** - Key findings and recommendations
2. **Assessment Overview** - Scope, objectives, and methodology
3. **Risk Summary** - Vulnerability overview by severity
4. **Detailed Findings** - Complete vulnerability descriptions with:
   - Evidence and proof of concept
   - Impact assessment
   - Remediation recommendations
   - Business impact analysis
5. **Recommendations** - Prioritized action items
6. **Conclusion** - Summary and key takeaways
7. **Appendix** - Methodology, tools, and references

---

## OWASP Top 10 2021 Coverage

The identified vulnerabilities map to the following OWASP categories:

- **A01: Broken Access Control** - CSRF, Path Traversal, State Manipulation
- **A02: Cryptographic Failures** - Insecure Password Transmission
- **A03: Injection** - Cross-Site Scripting (XSS)
- **A05: Security Misconfiguration** - Missing Headers, File Upload, Info Disclosure
- **A07: Authentication Failures** - Missing Rate Limiting

---

## Recommendations Priority

### Immediate (24 hours)
1. Fix password transmission (use POST, not URL parameters)
2. Enable HTTPS for all authentication operations

### Short-Term (30 days)
1. Implement security headers (CSP, X-Frame-Options, HSTS)
2. Fix XSS vulnerabilities with input validation
3. Secure password fields (mask input)
4. Implement CSRF protection

### Medium-Term (90 days)
1. Implement rate limiting on authentication
2. Secure file upload functionality
3. Fix path traversal vulnerabilities
4. Move authorization checks server-side

---

## About Google Gruyere

Google Gruyere is an intentionally vulnerable web application developed by Google for security training and education purposes. It contains various security vulnerabilities designed to help developers and security professionals learn about web application security in a safe, legal environment.

**Important:** The vulnerabilities identified in this report are specific to this training application. Similar vulnerabilities in production systems would pose significant security risks.

---

## References

- [OWASP Top 10:2021](https://owasp.org/Top10/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Google Gruyere](https://google-gruyere.appspot.com/)
- [CVSS v3.1 Calculator](https://www.first.org/cvss/calculator/3.1)

---

## Disclaimer

This assessment was conducted in a read-only manner using passive scanning techniques only. No active exploitation, brute force attacks, or denial-of-service testing was performed. The assessment was conducted on an intentionally vulnerable application designed for educational purposes with explicit authorization.

---

## License

This report is created for educational purposes as part of a cybersecurity internship task.

---

**Prepared by:** Purnendu Rai  
**Date:** March 22, 2026  
**Classification:** Confidential - For Educational Purposes

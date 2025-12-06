# Security Policy

## Reporting a Security Vulnerability

**⚠️ Please do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.**

We take security seriously and appreciate your efforts to responsibly disclose your findings.

---

## How to Report

### Email Us Directly

**Send reports to:** [security@admiral.io](mailto:security@admiral.io)

**Use this email for:**

- Security vulnerabilities in Admiral
- Potential security issues in our infrastructure
- Authentication or authorization bypasses
- Data exposure risks
- Any security-related concerns

### PGP Encryption (Optional)

For sensitive disclosures, you may encrypt your report using our PGP key:

```
[PGP Public Key Fingerprint - Add yours here]
[Link to public key]
```

---

## What to Include in Your Report

To help us understand and address the issue quickly, please include:

### Required Information

- **Description of the vulnerability**
  - What is the issue?
  - What is the potential impact?
- **Steps to reproduce**
  - Detailed steps to trigger the vulnerability
  - Any specific configurations required
- **Proof of concept**
  - Code snippets, screenshots, or videos
  - Example requests/responses (if applicable)

### Helpful Additional Information

- **Affected components**
  - Which parts of Admiral are affected?
  - Infrastructure provisioning, deployment, API, UI, etc.
- **Attack scenario**
  - How could this be exploited?
  - What's the worst-case scenario?
- **Suggested remediation**
  - If you have ideas for how to fix it, we'd love to hear them
- **Your environment**
  - Admiral version
  - Cloud provider(s)
  - Kubernetes distribution

---

## Our Response Process

### Timeline

| Stage                   | Timeframe                       |
| ----------------------- | ------------------------------- |
| **Initial Response**    | Within 48 hours                 |
| **Triage & Assessment** | Within 5 business days          |
| **Status Updates**      | Every 7 days until resolved     |
| **Fix Development**     | Based on severity (see below)   |
| **Public Disclosure**   | After fix is deployed + 90 days |

### Severity-Based Response Times

**Critical Severity**

- Issues that allow unauthorized access to customer data or infrastructure
- Remote code execution vulnerabilities
- Authentication bypasses
- **Target Fix:** 7-14 days

**High Severity**

- Privilege escalation within Admiral
- SQL injection or similar injection vulnerabilities
- Cross-site scripting (XSS) in authenticated contexts
- **Target Fix:** 14-30 days

**Medium Severity**

- Information disclosure of non-sensitive data
- Denial of service vulnerabilities
- Cross-site request forgery (CSRF)
- **Target Fix:** 30-60 days

**Low Severity**

- Issues with minimal security impact
- Configuration weaknesses
- **Target Fix:** 60-90 days

---

## What Happens After You Report

1. **We acknowledge your report** within 48 hours

   - Confirmation that we received it
   - Initial assessment of severity
   - Assignment of a tracking ID

2. **We investigate and validate** the issue

   - Reproduce the vulnerability
   - Assess impact and scope
   - Determine affected versions

3. **We develop and test a fix**

   - Create a patch
   - Test thoroughly across environments
   - Prepare deployment plan

4. **We deploy the fix**

   - Roll out to all affected systems
   - Verify the issue is resolved
   - Monitor for any edge cases

5. **We coordinate disclosure**
   - Notify you when the fix is deployed
   - Work with you on public disclosure timing
   - Credit you in our security advisory (if desired)

---

## Disclosure Policy

### Our Commitment

- We will keep you informed throughout the process
- We will credit you for your discovery (unless you prefer to remain anonymous)
- We will not take legal action against researchers who follow this policy

### Coordinated Disclosure

We follow a **90-day disclosure timeline**:

- **Day 0:** Vulnerability reported
- **Day 1-14:** Fix developed and tested
- **Day 15-30:** Fix deployed to production
- **Day 90+:** Public disclosure (security advisory published)

We may request extended timelines for complex issues, but will work with you to find a reasonable disclosure date.

### Public Disclosure

Once a fix is deployed and sufficient time has passed:

1. We publish a security advisory in our [GitHub Security Advisories](https://github.com/DataliftHQ/admiral-community/security/advisories)
2. We credit the researcher (with permission)
3. We update our changelog and release notes
4. We notify affected customers directly

---

## Supported Versions

We provide security updates for the following versions:

| Version | Supported                                |
| ------- | ---------------------------------------- |
| 1.x     | ✅ Fully supported                       |
| 0.9.x   | ⚠️ Critical fixes only (EOL: March 2025) |
| < 0.9   | ❌ No longer supported                   |

**Recommendation:** Always run the latest version of Admiral to receive the most up-to-date security patches.

---

## Scope

### In Scope

The following are within the scope of our security program:

✅ **Admiral Platform**

- Web application (admiral.io)
- API endpoints
- Authentication and authorization mechanisms
- Kubernetes agent components
- Terraform module execution

✅ **Data Security**

- Customer data exposure
- Infrastructure credentials handling
- Secrets management
- Access control vulnerabilities

✅ **Infrastructure**

- Our hosted services
- Deployment pipelines
- Container security

### Out of Scope

The following are generally **not** considered security vulnerabilities:

❌ **Non-security bugs**

- Use the [bug report template](https://github.com/DataliftHQ/admiral-community/issues/new?template=bug_report.yml) instead

❌ **Social engineering**

- Phishing attacks against Admiral employees
- Physical attacks against our offices

❌ **Denial of Service**

- Automated scanning or excessive requests
- Resource exhaustion through normal use

❌ **Third-party services**

- Vulnerabilities in dependencies (unless exploitable in Admiral's context)
- Issues with cloud providers (AWS, GCP, Azure)

❌ **Issues requiring significant user interaction**

- Self-XSS
- Attacks requiring physical access to a user's machine

**When in doubt, please report it.** We'd rather review a non-issue than miss a real vulnerability.

---

## Bug Bounty Program

### Current Status

We do not currently operate a formal bug bounty program. However, we deeply appreciate security research and will:

- **Publicly acknowledge** your contribution (with permission)
- **Send Admiral swag** for valid reports
- **Provide references** for security researchers
- Consider **financial rewards** for critical vulnerabilities on a case-by-case basis

We are evaluating a formal bug bounty program for 2025. Stay tuned!

---

## Safe Harbor

Admiral is committed to working with security researchers under the following safe harbor policy:

**We will not pursue legal action** against researchers who:

✅ Make a good faith effort to comply with this policy
✅ Do not access, modify, or delete customer data beyond what's necessary to demonstrate the vulnerability
✅ Do not intentionally harm Admiral's operations or customers
✅ Give us reasonable time to fix the issue before public disclosure
✅ Do not exploit the vulnerability beyond what's necessary for proof of concept

**Legal safe harbor applies to:**

- Vulnerability research conducted on your own account/infrastructure
- Responsible disclosure following this policy
- Good faith security testing

**Legal safe harbor does NOT apply to:**

- Testing on production customer data without authorization
- Intentional service disruption
- Social engineering of employees or customers
- Physical attacks

---

## Security Best Practices for Admiral Users

While we work to keep Admiral secure, here are recommendations for users:

### For Platform Teams

- **Enable audit logging** for all infrastructure provisioning
- **Review module permissions** regularly
- **Use least-privilege access** for service accounts
- **Rotate credentials** periodically
- **Monitor for unusual activity** in Admiral logs

### For Application Teams

- **Don't commit secrets** to your application manifests
- **Use Admiral's secrets management** instead of plain text
- **Review deployment logs** for unexpected changes
- **Keep your Kubernetes agents updated**

### For Administrators

- **Enable SSO/SAML** for centralized authentication
- **Use strong password policies**
- **Enable two-factor authentication** for all users
- **Regularly review user permissions**
- **Subscribe to security advisories** (watch this repository)

---

## Security Resources

- **Security Advisories:** [GitHub Security Advisories](https://github.com/DataliftHQ/admiral-community/security/advisories)
- **Security Documentation:** [docs.admiral.io/security](https://docs.admiral.io/security)
- **Compliance:** [admiral.io/compliance](https://admiral.io/compliance)
- **Status Page:** [status.admiral.io](https://status.admiral.io)

---

## Contact

### Security Team

**Email:** [security@admiral.io](mailto:security@admiral.io)  
**Response Time:** Within 48 hours

### Other Security-Related Inquiries

- **Compliance questions:** [compliance@admiral.io](mailto:compliance@admiral.io)
- **Privacy questions:** [privacy@admiral.io](mailto:privacy@admiral.io)
- **General security questions:** [security@admiral.io](mailto:security@admiral.io)

---

## Acknowledgments

We would like to thank the following security researchers for their responsible disclosure:

- _Hall of Fame coming soon_

Want to be listed here? Help us keep Admiral secure by reporting vulnerabilities responsibly.

---

**Last Updated:** December 6, 2024

---

<div align="center">

**Thank you for helping keep Admiral and our users safe.**

[Report a Vulnerability](mailto:security@admiral.io) • [Security Documentation](https://docs.admiral.io/security)

</div>
```

---

## Implementation Checklist

### 1. **Set Up Security Email**

- [ ] Create `security@admiral.io` email address
- [ ] Route to security-responsible team members
- [ ] Set up auto-responder acknowledging receipt
- [ ] Create internal response playbook

### 2. **Optional: PGP Key**

- [ ] Generate PGP key for encrypted communications
- [ ] Publish public key
- [ ] Add fingerprint to SECURITY.md
- [ ] Document key management process internally

### 3. **Internal Process Documentation**

Create an internal security runbook:

- Who receives security reports
- Severity classification criteria
- Escalation procedures
- Communication templates
- Deployment procedures for fixes

### 4. **GitHub Security Features**

Enable these in your repository:

**Settings → Security:**

- [ ] Enable "Private vulnerability reporting"
- [ ] Set up security policy (links to this SECURITY.md)
- [ ] Enable Dependabot alerts
- [ ] Enable code scanning (if applicable)

### 5. **Communication Templates**

**Initial Response (within 48 hours):**

```
Subject: [SECURITY-####] Acknowledgment of Security Report

Thank you for reporting this security issue to Admiral.

Tracking ID: SECURITY-####
Received: [Date/Time]
Initial Severity Assessment: [Critical/High/Medium/Low]

We are investigating and will provide an update within 5 business days.

If you have additional information, please reply with your tracking ID.

Best regards,
Admiral Security Team
security@admiral.io
```

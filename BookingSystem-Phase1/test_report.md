# 1️ Introduction

**Tester(s):**  
- Name: Stanislau Patapau  

**Purpose:**  
- Evaluate the security and functionality of the Booking System Phase 1, focusing on the registration feature.  
- Identify vulnerabilities, anomalies, and insecure behaviors in the registration flow.

**Scope:**  
- Tested components: Registration page, client-side behavior, backend registration logic, form validation, request handling.  
- Exclusions: Login (non-functional), admin features, reservation features, resource management, role-based functionality.  
- Test approach: Gray-box testing.

**Test environment & dates:**  
- Start:  
- End:  
- Environment: Local Docker environment (Phase1 Part1 compose stack), browser tested using Chrome Version 131, Host OS: Windows.  
- Runtime: Python backend (provided by course materials).  
- Database: PostgreSQL (Docker container).  

**Assumptions & constraints:**  
- Only registration is implemented in Phase 1.  
- Login functionality is broken and cannot be tested.  
- Limited to local environment; HTTPS not available.  

---

# 2️ Executive Summary

**Short summary:**  
The registration functionality contains multiple high-impact vulnerabilities, including stored XSS, SQL injection through password fields, missing server-side validation, no CSRF protection, no HTTPS, and broken login functionality.

**Overall risk level:** Critical

**Top 5 immediate actions:**  
1. Implement server-side validation for all input fields.  
2. Sanitize and encode user input to prevent XSS.  
3. Implement CSRF protection on all POST endpoints.  
4. Enforce password policy and restrict invalid data (e.g., negative age).  
5. Fix the login system and introduce proper session handling with secure cookies.  

---

# 3️ Severity scale & definitions

| Severity | Description | Recommended Action |
|---------|-------------|--------------------|
| 🔴 High | Serious vulnerability leading to compromise or data exposure (SQL injection, stored XSS). | Fix immediately |
| 🟠 Medium | Significant weakness requiring specific conditions (CSRF, weak validation). | Fix as soon as possible |
| 🟡 Low | Minor issue, weak policy, missing configuration. | Fix soon |
| 🔵 Info | No direct risk, informational only. | Monitor |

---

# 4️ Findings

| ID | Severity | Finding | Description | Evidence / Proof |
|----|----------|----------|--------------|------------------|
| F-01 | 🔴 High | Stored XSS in password field | Registration accepts JavaScript payloads and stores them in DB without sanitization. | Payloads `<script>alert(1)</script>`, `"><script>alert(1)</script>`, `<IMG SRC=x onerror=alert(1)>` all register successfully. |
| F-02 | 🔴 High | SQL Injection through password field | Password field accepts SQL payloads such as `' OR 1=1 --` and `' OR 'a'='a` without sanitization. | All SQL payloads succeed except `test@example.com');--`. |
| F-03 | 🟠 Medium | Missing CSRF protection | Registration POST request contains no CSRF token and can be forged via crafted requests. | No CSRF token found in request headers or form data. |
| F-04 | 🟠 Medium | Weak or missing input validation | Age accepts negative values and unrealistic values. Password accepts extremely weak values. | Registration succeeds with age “-5” and password “1”. |
| F-05 | 🔴 High | No HTTPS (Insecure Transport) | All registration data transmitted in plain text via HTTP. | Application served at `http://localhost:8000`. |
| F-06 | 🔴 High | Login functionality broken | Login button does nothing, no POST request is sent, system cannot authenticate users. | Login produces no network activity. |

---

# 5️ OWASP ZAP Test Report (Attachment)

**Purpose:**  
The OWASP ZAP scan should be attached as a separate Markdown file (`zap_report.md`).  
It supplements manual testing with automated vulnerability detection.

**Instructions:**  
1. Run the ZAP scan against your local environment.  
2. Export as Markdown.  
3. Save as `BookingSystem-Phase1/zap_report.md`.  
4. Add file to your Git repository.

**Attach/link the ZAP report here:**  
- `zap_report.md`

---

# End of Report

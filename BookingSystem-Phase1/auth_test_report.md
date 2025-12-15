# Authorization Test Report

Student: Stanislau Patapau  
Application: cybersec-phase3  
Base URL: http://localhost:8003  
Testing method: Manual authorization testing using browser and PowerShell (curl / Invoke-WebRequest)

---

## Completed List

The following steps were completed according to the assignment requirements:

- Started Phase 3 using Docker Compose
- Verified application is accessible on http://localhost:8003
- Registered a new user account
- Logged in successfully
- Identified available endpoints:
  - /login
  - /register
  - /resources
  - /reservation
  - /session
- Collected session cookies after login:
  - csrf_token
  - session_id
- Tested endpoints using PowerShell:
  - With valid session cookies
  - Without any cookies
- Compared HTTP responses (status codes and content)

---

## Findings

### 1. `/resources`

**Tested with cookie**
- Request: GET /resources
- Result: HTTP 200 OK
- Response: HTML page ("Manage Resources")

**Tested without cookie**
- Request: GET /resources
- Result: HTTP 200 OK
- Response: Same HTML page

**Finding**
- The `/resources` endpoint is accessible without authentication.
- No difference between authenticated and unauthenticated responses.
- If resource management is intended to be restricted, authorization is missing.

---

### 2. `/reservation`

**Tested with cookie**
- Request: GET /reservation
- Result: HTTP 200 OK
- Response: HTML page

**Tested without cookie**
- Request: GET /reservation
- Result: HTTP 200 OK
- Response: Same HTML page

**Finding**
- The `/reservation` endpoint returns identical content regardless of authentication state.
- No server-side authorization enforcement observed.

---

### 3. `/session`

**Tested with cookie**
- Request: GET /session
- Result: HTTP 200 OK
- Response: HTML status page

**Tested without cookie**
- Request: GET /session
- Result: HTTP 200 OK
- Response: Same HTML page

**Finding**
- Session status page is accessible without authentication.
- Session-based authorization checks are not enforced at the endpoint level.

---

### 4. `/recourses` (as tested)

**Tested with cookie and XHR headers**
- Request: GET /recourses
- Result: HTTP 200 OK
- Response: HTML page

**Tested without cookie**
- Request: GET /recourses
- Result: HTTP 200 OK
- Response: Same HTML page

**Finding**
- Endpoint returns HTML instead of JSON even when XHR headers are sent.
- No authorization checks detected.

---

## Summary of Role Capabilities

Based on testing results, the system currently behaves as follows:

| Role | Observed Capabilities |
|-----|----------------------|
| Unauthenticated user | Can access `/resources`, `/reservation`, `/session`, `/recourses` |
| Authenticated user | Receives the same responses as unauthenticated user |
| Authorization difference | None observed |

**Overall conclusion**
- No effective authorization separation between logged-in and non-logged-in users was observed.
- Endpoints do not enforce access control at the server level.
- If these pages are intended to expose user-specific or restricted functionality, authorization controls are missing.

---

## Final Conclusion

The application allows access to multiple endpoints without verifying authentication or authorization state.  
This indicates missing or incomplete authorization checks on the backend.  
Frontend access restrictions alone are not sufficient to protect sensitive functionality.


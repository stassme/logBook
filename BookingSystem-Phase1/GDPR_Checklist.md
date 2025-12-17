# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal data mapping and minimization** |
| :----: | :--- |
| ✅ | Have all personal data collected and processed in the system been identified (e.g., email, age, role, login credentials)? |
| ✅ | Have you ensured that only necessary personal data is collected (data minimization)? |
| ✅ | Is user age recorded to verify that the booker is over 15 years old? |

---

| **Result** | **User registration and management** |
| :----: | :--- |
| ⚠️ | Does the registration form include GDPR-compliant consent for processing personal data (acceptance of privacy policy)? |
| ⚠️ | Can users view, edit, and delete their own personal data via their account? |
| ✅ | Is there a mechanism for the administrator to delete a reserver in accordance with the right to be forgotten? |
| ✅ | Is underage registration (under 15 years) and booking functionality restricted? |

---

| **Result** | **Booking visibility** |
| :----: | :--- |
| ✅ | Are bookings visible to non-logged-in users only at the resource level (without any personal data)? |
| ✅ | Is it ensured that names, emails, or other personal data of bookers are not exposed publicly or to unauthorized users? |

---

| **Result** | **Access control and authorization** |
| :----: | :--- |
| ✅ | Have you ensured that only administrators can add, modify, and delete resources and bookings? |
| ✅ | Is the system using role-based access control (reserver vs administrator)? |
| ⚠️ | Are administrator privileges limited to ensure data is not used for unauthorized purposes? |

---

| **Result** | **Privacy by Design Principles** |
| :----: | :--- |
| ✅ | Has Privacy by Default been implemented by collecting only minimum required data? |
| ⚠️ | Are logs implemented without unnecessarily storing personal data? |
| ✅ | Are forms and system components designed with data protection in mind (secured login, minimal fields)? |

---

| **Result** | **Data security** |
| :----: | :--- |
| ⚠️ | Are CSRF, XSS, and SQL injection protections implemented? |
| ⚠️ | Are passwords securely hashed using a strong algorithm (bcrypt, Argon2)? |
| ⚠️ | Are data backup and recovery processes GDPR-compliant? |
| ⚠️ | Is personal data stored within the EU? |

---

| **Result** | **Data anonymization and pseudonymization** |
| :----: | :--- |
| ✅ | Is personal data anonymized where possible (public booking view)? |
| ⚠️ | Are pseudonymization techniques used for stored personal data? |

---

| **Result** | **Data subject rights** |
| :----: | :--- |
| ⚠️ | Can users request access to all personal data related to them? |
| ⚠️ | Is there a process for users to request deletion of their personal data? |
| ⚠️ | Can users withdraw consent for non-essential processing? |

---

| **Result** | **Documentation and communication** |
| :----: | :--- |
| ⚠️ | Is a privacy policy available during registration and easily accessible? |
| ⚠️ | Are data protection practices documented for administrators and developers? |
| ⚠️ | Is there a documented data breach response process? |

---

**Symbols used:**  
✅ Pass  
❌ Fail  
⚠️ Attention required

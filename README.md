# VulnBank: Horizontal Privilege Escalation

**A hands-on web application security assessment demonstrating unauthorized cross-user account access through session-token manipulation.**


## 🧭 Project Overview

This project documents a practical web application security lab performed on VulnBank.org to investigate horizontal privilege escalation and weaknesses in session-based access control.

Using Burp Suite, I examined two regular user sessions, Mary and Mike, and tested whether manipulating the session token in Mike's session could expose another user's account.

The test demonstrated that replacing Mike's session cookie with Mary's token caused the application dashboard to display Mary's account.

This highlighted the importance of secure session management and server-side authorization checks.

## 🎯 Objectives

- Understand horizontal privilege escalation in web applications.
- Examine how session tokens influence authenticated user access.
- Use Burp Suite to inspect and modify HTTP session data in a controlled lab.
- Document the observed security impact.
- Recommend measures to prevent unauthorized cross-user access.

## 🛠️ Tools and Environment

| Component    | Purpose                                        |
| ------------ | ---------------------------------------------- |
| VulnBank.org | Web application security lab target            |
| Burp Suite   | HTTP interception and session testing          |
| Web browser  | User authentication and dashboard verification |

## 🔬 Methodology

1. **Establish a baseline:** Logged in as Mary and observed her authenticated dashboard.
2. **Inspect another session:** Logged in as Mike and examined the session cookie using Burp Suite.
3. **Perform the test:** Replaced Mike's session cookie with Mary's token in the controlled lab.
4. **Verify the result:** Refreshed the application and observed that Mary's dashboard appeared in the session being tested.
5. **Analyze the impact:** Considered the implications for session isolation and authorization between different users.

## 📸 Evidence

### Video Demonstration

**Full practical walkthrough:** [https://drive.google.com/file/d/1C8vCY2yDMvlfP8OlkKZ1V6z2ccylEjoU/view?usp=drivesdk]

### Screenshots

**1. Mary's authenticated session**

This shows Mary's login request and the server's response containing a session token.

<img width="1267" height="401" alt="Project mary token" src="https://github.com/user-attachments/assets/56c1184a-eeda-4189-9370-53b9c9df8e3c" />

**2. Mike's authenticated session**

<img width="1266" height="342" alt="Mike project token" src="https://github.com/user-attachments/assets/5e010788-bc08-45b8-887e-9554cdb8052a" />

## 🔍 Security Analysis

The observed behavior indicates that a session-token substitution could result in access to another user's authenticated dashboard in the tested environment.

Horizontal privilege escalation involves gaining unauthorized access to resources belonging to another user at the same privilege level. In this demonstration, session-token manipulation was the technique used to test cross-user access.

The precise underlying vulnerability cannot be established from the dashboard result alone. Further authorized testing would be needed to determine whether the issue originates from session validation, token handling, authorization enforcement, or another application weakness.

## 🛡️ Recommended Remediation

- **Enforce server-side authorization:** Verify that every requested resource belongs to the authenticated user or that access is explicitly authorized.
- **Protect session tokens:** Use secure cookie attributes, HTTPS, appropriate token lifetimes, and safe session invalidation.
- **Prevent session confusion:** Ensure that session identifiers are securely generated, validated, and bound to the correct authenticated session.
- **Validate object ownership:** Check user permissions on every sensitive request instead of relying on client-side controls.
- **Log suspicious activity:** Monitor unexpected session changes and repeated unauthorized access attempts.

## 🧠 Key Learnings

Through this exercise, I gained practical experience with:

- Horizontal privilege escalation concepts.
- HTTP session cookies and authentication state.
- Intercepting and modifying requests with Burp Suite.
- Recognizing potential access-control weaknesses.
- Documenting security findings and proposing remediation.

## ⚖️ Ethical Scope

This project is intended for educational and portfolio purposes. Testing should only be conducted in an authorized lab or environment where explicit permission has been granted. No real user credentials or session tokens should be published.

## 👨‍💻 Author

**Samuel Miracle**
Cybersecurity | Web Application Security | Penetration Testing

[GitHub Profile](https://github.com/SC814)) · [LinkedIn Profile](https://www.linkedin.com/in/samuel-miracle-1a7725338))

*Learning by testing, documenting, and improving security.*

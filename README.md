# Linux STIG-Based System Hardening Project

## Project Overview

This project demonstrates hands-on Linux system hardening aligned with DISA STIG (Security Technical Implementation Guide) principles.

The objective was to secure an Ubuntu 24.04 LTS virtual machine by applying security controls related to:

- SSH hardening
- Password complexity enforcement
- Account lockout policies
- Password aging
- Sudo logging
- Audit logging
- File permission auditing
- Login banners

This project simulates a DoD-aligned secure configuration environment.

---

## Environment

- OS: Ubuntu 24.04 LTS
- Platform: Virtual Machine
- User: kevin
- Kernel: 6.8.x
- Architecture: aarch64

---

# 1️⃣ SSH Service Enablement

Enabled and verified OpenSSH service.

![SSH Service Enabled](screenshots/ssh-service-enabled.png)

---

# 2️⃣ SSH Configuration Hardening

Modified `/etc/ssh/sshd_config` with STIG-aligned settings:

- PermitRootLogin no
- MaxAuthTries 3
- X11Forwarding no
- LoginGraceTime 30
- Banner /etc/issue.net

![SSH Config Changes](screenshots/sshd-config.png)

Restarted SSH service:

![SSH Restart](screenshots/ssh-service-restart.png)

---

# 3️⃣ Login Banner Implementation

Created and verified a legal login banner.

![Banner Creation](screenshots/banner-creation-verification.png)

Verified banner configuration from remote connection:

![Banner Remote Verification](screenshots/banner-verification-mac.png)

---

# 4️⃣ Password Complexity Enforcement (pwquality)

Configured `/etc/security/pwquality.conf`:

- minlen = 14
- difok = 4
- minclass = 4
- maxrepeat = 3

![Password Policy](screenshots/pwquality-password.png)

---

# 5️⃣ Password Aging Policy

Modified `/etc/login.defs`:

- PASS_MAX_DAYS 60
- PASS_MIN_DAYS 1
- PASS_WARN_AGE 7

![Password Aging](screenshots/password-policy.png)

Verified settings:

![Password Aging Verification](screenshots/more-password-policy.png)

---

# 6️⃣ Account Lockout Policy (Faillock)

Configured `/etc/pam.d/common-auth` and `/etc/security/faillock.conf`:

- deny = 3
- unlock_time = 900
- audit

![Faillock Config](screenshots/faillock-implemenatation.png)

Verification:

![Faillock Verification](screenshots/faillock-implementation-verification.png)

Confirmed root lock enforcement:

![Root Lock Verification](screenshots/verification-root-locked.png)

---

# 7️⃣ Sudo Logging Enforcement

Modified `/etc/sudoers` to log all sudo activity:

- Defaults logfile="/var/log/sudo.log"

Verified sudo logging:

![Sudo Logging](screenshots/sudo-logging-enforced.png)

Log verification:

![Sudo Log Verification](screenshots/sudo-logging-enforced.png)

---

# 8️⃣ Auditd Enablement

Installed and enabled auditd service.

![Audit Service Enabled](screenshots/enable-audit-logging.png)

Verified audit logs:

![Audit Logs](screenshots/audit-logs-verification.png)

---

# 9️⃣ World-Writable File Scan

Scanned for insecure world-writable files:

![World Writable Scan](screenshots/scanning-world-writable.png)

---

# Security Impact

The applied controls mitigate:

- Brute force attacks
- Privilege escalation
- Weak password usage
- Unauthorized root access
- Insider misuse
- Lack of audit visibility
- Improper file permissions

This configuration significantly improves system security posture and aligns with STIG hardening standards.

---

# Skills Demonstrated

- Linux system administration
- STIG interpretation and implementation
- SSH hardening
- PAM configuration
- Account lockout mechanisms
- Audit logging configuration
- Sudo policy enforcement
- File permission auditing
- Security documentation

---

# Author

Kevin Minaya  
Cybersecurity Professional  

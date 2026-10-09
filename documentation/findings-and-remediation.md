# Technical findings and remediation

## F-01: Exposed web backup directory

**Observation:** The report describes a publicly accessible `/backup` path with directory listing enabled.

**Impact:** Unauthenticated visitors may enumerate and retrieve files stored there.

**Remediation:** Store backups outside the document root, disable autoindexing, restrict directory access, and verify with an unauthenticated test.

## F-02: Plaintext credentials in backup artifact

**Observation:** The original report documents a `mysql.bak` file with application database credentials in plaintext.

**Impact:** Credential exposure could permit unauthorized database access or facilitate credential reuse if other controls fail. No such access was established by this report.

**Remediation:** Remove the file from web-accessible locations, rotate exposed credentials, enforce least privilege, and audit access logs.

## F-03: Unsuccessful SSH access attempt

**Observation:** A limited SSH credential-reuse test failed.

**Interpretation:** This does not establish the reason for failure, nor prove that SSH is secure against other techniques.

**Remediation:** Review SSH configuration, restrict login methods and source networks, and monitor failed authentications.

## Assessment boundary

All activity described was limited to an authorized, intentionally vulnerable training VM. No successful privilege escalation or `flag.txt` recovery was established in the source report.

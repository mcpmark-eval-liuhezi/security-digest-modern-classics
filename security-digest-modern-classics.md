# Modern Classics — Quarterly Open-Source Security Digest: Retrospective on Four incidents every developer should know by name

## Apache Log4j "Log4Shell" — CVE-2021-44228
![Apache Log4j logo](https://upload.wikimedia.org/wikipedia/commons/f/f9/Apache_Log4j_Logo.png)

- **CVE:** CVE-2021-44228
- **GitHub Advisory (GHSA):** GHSA-jfh8-c2jp-5v3q — https://github.com/advisories/GHSA-jfh8-c2jp-5v3q
- **Severity / CVSS:** Critical — CVSS 10.0 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H/E:H). NVD base score 10.0 CRITICAL.
- **First fixed version:** 2.15.0 (initial fix); complete fix in 2.16.0 (JNDI lookups disabled by default and message lookups removed); backports in 2.3.1, 2.12.2, 2.12.3
- **Disclosure year:** 2021 (December 2021; NVD published 2021-12-10)
- **Authoritative link:** https://nvd.nist.gov/vuln/detail/CVE-2021-44228 (advisory page: https://github.com/advisories/GHSA-jfh8-c2jp-5v3q)
- **What to tell your team:** Any `log4j-core` <= 2.14.1 is endangered — upgrade to >= 2.16.0; meanwhile set `log4j2.formatMsgNoLookups=true` and watch logs for LDAP/JNDI payload patterns.

## OpenSSL "Heartbleed" — CVE-2014-0160
![OpenSSL logo](https://upload.wikimedia.org/wikipedia/commons/a/a1/OpenSSL_logo.png)

- **CVE:** CVE-2014-0160
- **GitHub Advisory (GHSA):** GHSA-w8r8-w5w4-4w4v — https://github.com/advisories/GHSA-w8r8-w5w4-4w4v (unreviewed record published to the GitHub Advisory Database 2022-05-13; no package-level fixed versions listed in the advisory)
- **Severity / CVSS:** High — CVSS 7.5 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N). NVD base score 5.0.
- **First fixed version:** OpenSSL 1.0.1g (and 1.0.2a on the 1.0.2 branch)
- **Disclosure year:** 2014 (April 2014; NVD published 2014-04-07)
- **Authoritative link:** https://nvd.nist.gov/vuln/detail/CVE-2014-0160 (advisory page: https://github.com/advisories/GHSA-w8r8-w5w4-4w4v; vendor advisory: https://www.openssl.org/news/secadv_20140407.txt)
- **What to tell your team:** Heartbleed leaks process memory (private keys, tokens), it is not remote code execution; rebuild 1.0.1/1.0.2 to >= 1.0.1g/1.0.2a and rotate any secrets that may have been exfiltrated from memory or backups.

## GNU Bash "Shellshock" — CVE-2014-6271
![GNU Bash logo](https://thumb.wikimedia.org/wikipedia/commons/thumb/8/82/Gnu-bash-logo.svg/3840px-Gnu-bash-logo.svg.png)

- **CVE:** CVE-2014-6271
- **GitHub Advisory (GHSA):** GHSA-6hfc-grwp-2p9c — https://github.com/advisories/GHSA-6hfc-grwp-2p9c (unreviewed record published to the GitHub Advisory Database 2022-05-13; no package-level fixed versions listed in the advisory)
- **Severity / CVSS:** Critical — CVSS 9.8 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H). NVD base score 5.0.
- **First fixed version:** GNU Bash 4.3 (the initial 4.3 fix was itself incorrect; CVE-2014-7169 covers the residual flaw)
- **Disclosure year:** 2014 (September 2014; NVD published 2014-09-24)
- **Authoritative link:** https://nvd.nist.gov/vuln/detail/CVE-2014-6271 (advisory page: https://github.com/advisories/GHSA-6hfc-grwp-2p9c; lcamtuf notes: http://lcamtuf.blogspot.com/2014/09/quick-notes-about-bash-bug-its-impact.html)
- **What to tell your team:** Environment variable parsing injected command substitution; upgrade to bash >= 4.3 and audit sudo/SSH ForceCommand/mod_cgid contexts — note the original 4.3 fix was incomplete (CVE-2014-7169).

## xz utils backdoor — CVE-2024-3094
![XZ logo](https://upload.wikimedia.org/wikipedia/commons/6/67/XZ_logo_contributed_by_Jia_Tan.png)

- **CVE:** CVE-2024-3094
- **GitHub Advisory (GHSA):** GHSA-rxwq-x6h5-x525 — https://github.com/advisories/GHSA-rxwq-x6h5-x525
- **Severity / CVSS:** Critical — CVSS 10.0 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H). NVD base score 10.0 CRITICAL.
- **First fixed version:** 5.6.1 (and 5.4.1 for the 5.4.x line); malicious code was present in upstream tarballs starting with 5.6.0, fixed in 5.6.1
- **Disclosure year:** 2024 (March 2024; announced 2024-03-28 via the oss-security mailing list)
- **Authoritative link:** https://nvd.nist.gov/vuln/detail/CVE-2024-3094 (advisory page: https://github.com/advisories/GHSA-rxwq-x6h5-x525; oss-security announcement: https://www.openwall.com/lists/oss-security/2024/03/29/4)
- **What to tell your team:** This was a supply-chain compromise, not a code bug — pin and verify checksums/signatures of xz/liblzma releases, use 5.6.1+ (or 5.4.1+), and treat any 5.6.0/5.6.1 binary as compromised.

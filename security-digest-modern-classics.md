# Modern Classics — Quarterly Security Digest: Library & Supply-Chain Bugs Every Developer Should Know

## Apache Log4j "Log4Shell" — CVE-2021-44228

![Apache Log4j](https://upload.wikimedia.org/wikipedia/commons/f/f9/Apache_Log4j_Logo.png)

- **CVE:** CVE-2021-44228
- **GitHub Advisory Database id:** GHSA-jfh8-c2jp-5v3q (reviewed entry)
- **Severity / CVSS:** Critical — CVSS 3.1 base score 10.0, vector `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H/E:H`
- **First fixed version:** 2.15.0 (initial fix); complete fix in 2.16.0, which disables JNDI lookups by default and removes message-lookup support; backports in 2.3.1, 2.12.2, 2.12.3
- **Disclosure year:** 2021 (December 2021; NVD published 2021-12-10)
- **Authoritative link:** https://github.com/advisories/GHSA-jfh8-c2jp-5v3q (NVD mirror: https://nvd.nist.gov/vuln/detail/CVE-2021-44228)
- **Logo:** ![Apache Log4j](https://upload.wikimedia.org/wikipedia/commons/f/f9/Apache_Log4j_Logo.png)

What to tell your team: Any log4j-core <= 2.14.1 is endangered — upgrade to 2.16.0+ (or a backport such as 2.12.2/2.3.1); meanwhile set `log4j2.formatMsgNoLookups=true` and watch logs for LDAP/JNDI payload patterns. Log4j 1.x is EOL and receives no fix for this class of issue.

## OpenSSL "Heartbleed" — CVE-2014-0160

![OpenSSL](https://upload.wikimedia.org/wikipedia/commons/a/a1/OpenSSL_logo.png)

- **CVE:** CVE-2014-0160
- **GitHub Advisory Database id:** GHSA-w8r8-w5w4-4w4v (unreviewed entry; no reviewed advisory exists for this CVE)
- **Severity / CVSS:** High per GitHub advisory database (CVSS 3.1 7.5, vector `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N`); NVD lists 5.5 MEDIUM (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N)
- **First fixed version:** OpenSSL 1.0.1g (April 2014) for the 1.0.1 branch; 1.0.2-beta2 (July 2014) for the 1.0.2 branch
- **Disclosure year:** 2014 (announced April 7, 2014; NVD published 2014-04-07)
- **Authoritative link:** https://github.com/advisories/GHSA-w8r8-w5w4-4w4v (NVD mirror: https://nvd.nist.gov/vuln/detail/CVE-2014-0160; vendor: https://www.heartbleed.com/)
- **Logo:** ![OpenSSL](https://upload.wikimedia.org/wikipedia/commons/a/a1/OpenSSL_logo.png)

What to tell your team: Heartbleed is a TLS heartbeat buffer over-read that leaks process memory (private keys, session tokens); patch to 1.0.1g or 1.0.2-beta2+, restart services, and reissue certificates — it needs no user interaction to exploit.

## GNU Bash "Shellshock" — CVE-2014-6271

![GNU Bash](https://thumb.wikimedia.org/wikipedia/commons/thumb/8/82/Gnu-bash-logo.svg/3840px-Gnu-bash-logo.svg.png)

- **CVE:** CVE-2014-6271
- **GitHub Advisory Database id:** GHSA-6hfc-grwp-2p9c (unreviewed entry; no reviewed advisory exists for this CVE)
- **Severity / CVSS:** Critical per GitHub advisory database; 9.8 CRITICAL per NVD (CVSS 3.1 `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H`)
- **First fixed version:** GNU Bash 4.3 (patch bash43-025, Sept 24 2014; official 4.3 release October 2014); distro backports (e.g., 4.2-2ubuntu2.x, 4.3-7ubuntu1.x)
- **Disclosure year:** 2014 (publicly disclosed September 2014; NVD published 2014-09-24)
- **Authoritative link:** https://github.com/advisories/GHSA-6hfc-grwp-2p9c (NVD mirror: https://nvd.nist.gov/vuln/detail/CVE-2014-6271; Red Hat guidance: https://access.redhat.com/articles/1200223)
- **Logo:** ![GNU Bash](https://thumb.wikimedia.org/wikipedia/commons/thumb/8/82/Gnu-bash-logo.svg/3840px-Gnu-bash-logo.svg.png)

What to tell your team: Bash through 4.3 processes trailing strings after function definitions in environment variables, allowing RCE across privilege boundaries (OpenSSH ForceCommand, Apache mod_cgi/mod_cgid, DHCP scripts). Upgrade to 4.3+ or backported versions; note the initial 4.3 fix was incomplete — CVE-2014-7169 covers the residual flaw.

## xz Utils Backdoor — CVE-2024-3094

![xz Utils](https://upload.wikimedia.org/wikipedia/commons/6/67/XZ_logo_contributed_by_Jia_Tan.png)

- **CVE:** CVE-2024-3094
- **GitHub Advisory Database id:** GHSA-rxwq-x6h5-x525 (unreviewed entry; no reviewed advisory exists for this CVE)
- **Severity / CVSS:** Critical — CVSS 3.1 base score 10.0, vector `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H` (NVD also rates 10.0; EPSS ~90.9%)
- **First fixed version:** xz 5.6.2 (upstream clean release, 2024-05-31); distros backported the fix to older series (e.g., Debian 1:5.6.0-1+)
- **Disclosure year:** 2024 (March 29, 2024; announced via oss-security 2024-03-29)
- **Authoritative link:** https://github.com/advisories/GHSA-rxwq-x6h5-x525 (NVD mirror: https://nvd.nist.gov/vuln/detail/CVE-2024-3094; Red Hat: https://access.redhat.com/security/cve/CVE-2024-3094)
- **Logo:** ![xz Utils](https://upload.wikimedia.org/wikipedia/commons/6/67/XZ_logo_contributed_by_Jia_Tan.png)

What to tell your team: Treat this as a supply-chain integrity problem, not a normal bug: verify tarball hashes against the upstream releases page, pin to 5.6.2+, and prefer distro-packaged xz where possible since backported copies may still carry the object-file injection.

---

*Digest generated from live GitHub Advisory Database records and NVD references. Logo images via Wikimedia Commons.*

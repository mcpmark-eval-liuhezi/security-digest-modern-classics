# Modern Classics — Quarterly Security Digest: Library & Supply-Chain Bugs Every Developer Should Know by Name

## Apache Log4j "Log4Shell" — CVE-2021-44228

![Apache Log4j logo](https://upload.wikimedia.org/wikipedia/commons/f/f9/Apache_Log4j_Logo.png)

- **CVE:** CVE-2021-44228
- **GitHub Advisory Database (GHSA):** GHSA-jfh8-c2jp-5v3q
- **Severity / CVSS:** Critical — CVSS 3.1 base score 10.0 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H/E:H)
- **First fixed version:** 2.15.0 (backports 2.3.1, 2.12.2, 2.12.3); 2.16.0 recommended as it disables JNDI by default and completely removes message-lookup support
- **Disclosure year:** 2021 (publicly disclosed December 10, 2021)
- **Authoritative link:** https://github.com/advisories/GHSA-jfh8-c2jp-5v3q
- **What to tell your team:** If you run Java apps on Log4j, treat 2.14.1 and earlier as compromised: upgrade to 2.16.0+ (or a 2.3.1/2.12.2 backport) and confirm JNDI lookup is disabled; note that Log4j 1.x is End-of-Life and receives no patch for this class of issue.

## OpenSSL "Heartbleed" — CVE-2014-0160

![OpenSSL logo](https://upload.wikimedia.org/wikipedia/commons/a/a1/OpenSSL_logo.png)

- **CVE:** CVE-2014-0160
- **GitHub Advisory Database (GHSA):** GHSA-w8r8-w5w4-4w4v
- **Severity / CVSS:** High — CVSS 3.1 base score 7.5 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:N/A:N)
- **First fixed version:** OpenSSL 1.0.1g (1.0.2 branch fixed in 1.0.2b)
- **Disclosure year:** 2014 (announced April 7, 2014)
- **Authoritative link:** https://github.com/advisories/GHSA-w8r8-w5w4-4w4v
- **What to tell your team:** Heartbleed leaks process memory via malformed heartbeat packets — private keys and session secrets are exposed. Upgrade to 1.0.1g or 1.0.2b or later, and audit every TLS endpoint (servers, load balancers, VPN termination points) because many were reinstallitted without the patch.

## GNU Bash "Shellshock" — CVE-2014-6271

![GNU Bash logo](https://upload.wikimedia.org/wikipedia/commons/8/82/Gnu-bash-logo.svg)

- **CVE:** CVE-2014-6271
- **GitHub Advisory Database (GHSA):** GHSA-6hfc-grwp-2p9c
- **Severity / CVSS:** Critical — CVSS 3.1 base score 9.8 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H)
- **First fixed version:** GNU Bash 4.3 (backports exist for older releases)
- **Disclosure year:** 2014 (publicly disclosed September 2014; note the initial fix was incomplete, with CVE-2014-7169 covering the residual flaw)
- **Authoritative link:** https://github.com/advisories/GHSA-6hfc-grwp-2p9c
- **What to tell your team:** Bash through 4.2 evaluates trailing strings after function definitions in environment variables — dangerous across privilege boundaries. Upgrade to 4.3+, or as a stopgap set `export BASH_ENV=/dev/null` and avoid passing untrusted env vars to shell scripts (impacts OpenSSH ForceCommand, Apache mod_cgi/mod_cgid, DHCP scripts, etc.).

## xz Utils Backdoor — CVE-2024-3094

![xz utils logo](https://upload.wikimedia.org/wikipedia/commons/6/67/XZ_logo_contributed_by_Jia_Tan.png)

- **CVE:** CVE-2024-3094
- **GitHub Advisory Database (GHSA):** GHSA-rxwq-x6h5-x525
- **Severity / CVSS:** Critical — CVSS 3.1 base score 10.0 (CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:C/C:H/I:H/A:H)
- **First fixed version:** xz 5.6.3 (liblzma 5.6.3; 5.6.4 also issued for liblzma)
- **Disclosure year:** 2024 (publicly disclosed March 29, 2024)
- **Authoritative link:** https://github.com/advisories/GHSA-rxwq-x6h5-x525
- **What to tell your team:** This was not a bug but an intentional supply-chain compromise: malicious .m4 build directives embedded in tarballs from 5.6.0 onward altered liblzma at build time. Trust no upstream xz tarball in the 5.6.0–5.6.2 range — verify checksums/signatures, rebuild from verified sources, and check every product linking liblzma (notably OpenSSH).

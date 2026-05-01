---
title: Release Notes and Change Logs
---

> **Ownership note:** This content was originally written for cPanel, L.L.C., and is owned by them. Technical writers owned all EasyApache 4 release note and change log content. Contributions to cPanel & WHM major version release notes were collaborative; sections I wrote are included here. Change log entries were formatted from developer-provided information using a prompt-based templating system I developed to ensure consistency and reduce formatting errors.

---

## Release Notes

Release notes summarize product changes for end users and link to full documentation for details. I wrote all EasyApache 4 release notes through December 2025. Entries for major cPanel & WHM versions were a team effort; the samples below are sections I wrote.

### EasyApache 4 25.31 — October 8, 2025

_Updated packages and security release_

We released updated packages for EasyApache 4.

This release includes updates to NodeJS 22, NGINX NJS, Tomcat 10.1, and Passenger. It also includes security updates for Ruby Rack, Redis, and Valkey to address [CVE-2025-61772](https://www.cve.org/CVERecord?id=CVE-2025-61772), [CVE-2025-61771](https://www.cve.org/CVERecord?id=CVE-2025-61771), [CVE-2025-61770](https://www.cve.org/CVERecord?id=CVE-2025-61770), [CVE-2025-49844](https://www.cve.org/CVERecord?id=CVE-2025-49844), [CVE-2025-46817](https://www.cve.org/CVERecord?id=CVE-2025-46817), [CVE-2025-46818](https://www.cve.org/CVERecord?id=CVE-2025-46818), and [CVE-2025-46819](https://www.cve.org/CVERecord?id=CVE-2025-46819).

For a full list of changes, read the EasyApache 4 change log.

---

### cPanel & WHM Version 132 — September 30, 2025 (excerpt)

#### Upgraded temporary domains for cPanel accounts

In cPanel & WHM version 132, we expanded the functionality of temporary domains for cPanel users. You can now create temporary domains for parked and addon domains, and convert your own temporary domain to a registered domain in cPanel's _Domains_ interface (_cPanel » Home » Domains » Domains_).

However, you **cannot** convert your account's main domain from a temporary domain to a registered domain. To make changes to your primary domain, contact your hosting provider.

---

## Change Log

Change log entries document individual package updates and security fixes at a technical level. I formatted these entries from developer-provided information for each EasyApache 4 release through December 2025.

### EasyApache 4 Change Log — Sample Entries

---

#### 25.32
_2025 October 16_

**ea-ruby27-rubygem-rack**
* EA-13188: Update `ea-ruby27-rubygem-rack` from 2.2.19 to 2.2.20.

**ea-tomcat101**
* EA-13164: Update `ea-tomcat101` from 10.1.45 to 10.1.46.

**ea-ruby27-passenger**
* EA-12915: Update `ea-ruby27-passenger` from 6.0.23 to 6.0.27.

**ea-nghttp2**
* EA-13175: Update `ea-nghttp2` from 1.67.0 to 1.67.1.

---

#### 25.31
_2025 October 08_

**ea-nodejs22**
* EA-13169: Update `ea-nodejs22` from 22.19.0 to 22.20.0.

**ea-cpanel-tools**
* EA4-112: Add `ea-wappspector` dependency.

**ea-wappspector**
* EA4-110: Initial version.

**ea-ruby27-rubygem-rack**
* EA-13174: Update `ea-ruby27-rubygem-rack` from 2.2.18 to 2.2.19 (with fixes for [CVE-2025-61772](https://www.cve.org/CVERecord?id=CVE-2025-61772), [CVE-2025-61771](https://www.cve.org/CVERecord?id=CVE-2025-61771), and [CVE-2025-61770](https://www.cve.org/CVERecord?id=CVE-2025-61770)).

**ea-nginx-njs**
* EA-13168: Update `ea-nginx-njs` from 0.9.1 to 0.9.3.

**ea-redis62**
* EA-13172: Update `ea-redis62` from 6.2.19 to 6.2.20 (with fixes for [CVE-2025-49844](https://www.cve.org/CVERecord?id=CVE-2025-49844), [CVE-2025-46817](https://www.cve.org/CVERecord?id=CVE-2025-46817), [CVE-2025-46818](https://www.cve.org/CVERecord?id=CVE-2025-46818), and [CVE-2025-46819](https://www.cve.org/CVERecord?id=CVE-2025-46819)).

**ea-valkey72**
* EA-13165: Update `ea-valkey72` from 7.2.10 to 7.2.11 (with fixes for [CVE-2025-49844](https://www.cve.org/CVERecord?id=CVE-2025-49844), [CVE-2025-46817](https://www.cve.org/CVERecord?id=CVE-2025-46817), [CVE-2025-46818](https://www.cve.org/CVERecord?id=CVE-2025-46818), and [CVE-2025-46819](https://www.cve.org/CVERecord?id=CVE-2025-46819)).

**ea-tomcat101**
* EA-13164: Update `ea-tomcat101` from 10.1.45 to 10.1.46.

**ea-passenger-src**
* EA-13128: Update `ea-passenger-src` from 6.0.27 to 6.1.0.

**ea-apache24-mod-passenger**
* EA-13128: `ea-passenger-src` was updated from 6.0.27 to 6.1.0.

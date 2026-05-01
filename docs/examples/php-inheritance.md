---
title: PHP Inheritance
---

> **Ownership note:** This document was originally written for cPanel, L.L.C., and is owned by them.

## Overview

In WHM's _MultiPHP Manager_ interface (_WHM » Home » Software » MultiPHP Manager_), the term "Inherit" refers to how Apache determines a domain or virtual host's PHP version.

When you set a cPanel account or domain to use the _Inherit_ option, Apache uses the PHP version that exists in the first `.htaccess` file that it finds in the domain's file structure. If the system **cannot** find an `.htaccess` file, Apache uses the system default PHP version. The system sets the PHP version of each new domain to the default value.

**Important:** The system enables PHP-FPM by default. You **cannot** set a cPanel account's PHP version to use the _Inherit_ option with PHP-FPM enabled.

## How Inheritance Works

PHP inheritance follows the following path:

1. You set the PHP version at the system level.

   **Important:** We **strongly** recommend that you only set the PHP version in WHM's _MultiPHP Manager_ interface (_WHM » Home » Software » MultiPHP Manager_). If you set your PHP version manually, you may experience unexpected behavior.

2. You set a cPanel account or domain to use the _Inherit_ option in WHM's _MultiPHP Manager_ interface (_WHM » Home » Software » MultiPHP Manager_).

3. Apache searches the cPanel & WHM default document root of the current domain and continues up the directory tree until it finds an `.htaccess` file with PHP version information.

   **Important:**
   * The document root location determines how your domain inherits its PHP version. For example, if a domain's document root is underneath a subdomain, the domain will inherit the subdomain's PHP version.
   * For a primary domain, the default document root is the `/$HOME/user/public_html` directory, where `/$HOME/` represents your home directory.
   * For a subdomain or addon domain, the default document root depends on your server's settings. For more information, read our _Tweak Settings_ documentation.
   * When you set a domain's PHP version, the system creates its `.htaccess` file.

4. Apache locates an `.htaccess` file with PHP version information.

5. Each cPanel account or domain set to _Inherit_ now uses the PHP version in the `.htaccess` file.

   **Note:**
   * If Apache does not find an `.htaccess` file, it uses the system default PHP version from WHM's _MultiPHP Manager_ interface (_WHM » Home » Software » MultiPHP Manager_).
   * If Apache finds an invalid version of PHP in the `.htaccess` file, it uses the system default PHP version set in WHM's _MultiPHP Manager_ interface (_WHM » Home » Software » MultiPHP Manager_).

## Examples

### Subdomains

In the following examples, the system uses PHP 8.2 by default.

**Note:** In the following table, the `sub3.example.com` and `sub4.example.com` domain examples are **only** valid if you set the _Restrict document roots to public\_html_ option in WHM's _Tweak Settings_ interface (_WHM » Home » Server Configuration » Tweak Settings_) to _Off_.

| Domain | Domain type | PHP setting | Effective PHP version | Document root within the `/public_html` directory |
| --- | --- | --- | --- | --- |
| `example.com` | Primary | 8.0 | 8.0 | Yes |
| `sub1.example.com` | Subdomain | 8.3 | 8.3 | Yes |
| `sub2.example.com` | Subdomain | Inherit | 8.3 — The `sub2.example.com` document root is underneath `sub1.example.com`, so it inherits from `sub1.example.com`. | Yes |
| `sub3.example.com` | Subdomain | Inherit | 8.2 | No |
| `sub4.example.com` | Subdomain | 8.2 | 8.2 | No |

| Domain | Domain type | PHP setting | Effective PHP version | Document root within the `/public_html` directory |
| --- | --- | --- | --- | --- |
| `domain.com` | Primary | Inherit | 8.2 | Yes |
| `sub5.domain.com` | Subdomain | Inherit | 8.2 | Yes |
| `sub6.domain.com` | Subdomain | 8.0 | 8.0 | Yes |

### Addon Domains

In the following examples, the system uses PHP 8.2 by default.

| Domain | Domain type | PHP setting | Effective PHP version | Document root within the `/public_html` directory |
| --- | --- | --- | --- | --- |
| `example.com` | Primary | 8.0 | 8.0 | Yes |
| `addon-example.com` | Addon | Inherit | 8.2 | Yes |

| Domain | Domain type | PHP setting | Effective PHP version | Document root within the `/public_html` directory |
| --- | --- | --- | --- | --- |
| `domain.com` | Primary | Inherit | 8.2 | Yes |
| `addon-example2.com` | Addon | Inherit | 8.2 | No |

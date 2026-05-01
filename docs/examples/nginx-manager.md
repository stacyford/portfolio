---
title: NGINX Manager
---

> **Ownership note:** This document was originally written for cPanel, L.L.C., and is owned by them. I was a member of the implementation team for this feature and wrote this documentation as part of that project.

---

## Overview

WHM's *NGINX® Manager* allows you to install, uninstall, and manage your NGINX with reverse proxy and caching server. You can also manage the caching on your server in this interface.

## Requirements

To install NGINX on your server, you **must** meet the following requirements:

* Run EasyApache 4.
* Possess `root` user access to the server.

**Note:**
* Previous versions of the `ea-nginx` package installed Apache's Passenger package by default. If you want to use Passenger, you must install the `ea-apache24-mod-passenger` package. If Passenger already exists on your server, it will remain on your server.

### Compatibility

NGINX takes the place of Apache as the primary web server. The installation will change Apache's default ports and assign those port numbers to NGINX.

**Note:** If you do not want to proxy all of your content through Apache, you can use the standalone version of NGINX.

### Limitations

cPanel & WHM's implementation of NGINX has the following limitations:

* If one of your domains matches a proxy domain, the system will warn you that it will ignore conflicting duplicate entries. This conflict may result in unexpected behavior.
* If you use NGINX and ModSecurity® 2, your ModSecurity rules **only** apply when NGINX proxies the request to Apache.
* NGINX redirects any non-SSL IPv6 requests to use SSL. This ensures that any IPv6-only service subdomains will work correctly. If your client will not accept the hostname's security certificate, we recommend that you use the subdomain's fully-qualified domain name instead.
* For security reasons, NGINX will **not** serve any file with a name starting with `.ht`.
* cPanel's *Optimize Website* interface (*cPanel » Home » Software » Optimize Website*) will **not** affect NGINX.
* If you create a custom NGINX configuration that uses the NGINX `alias` directive, make **certain** that your path's location ends with a trailing slash (`/`). If your path does **not** end with a `/`, then your path is vulnerable to a path traversal exploit.

## Landing Page

**Important:** This section of the interface **only** appears if NGINX is **not** installed on your server. If NGINX is already installed, the interface displays the [System Settings](#system-settings) tab.

To install NGINX on your server, click *Install*. A new interface will appear.

You can also use the EasyApache 4 interface, or run the following command on the command line as the `root` user:

| Operating System | Command |
| --- | --- |
| CentOS 7 | `yum install ea-nginx` |
| AlmaLinux OS and Rocky Linux™ | `dnf install ea-nginx` |
| Ubuntu® | `apt install --purge ea-nginx` |

**Note:** We also provide the *cPanel Default NGINX®* profile in WHM's *EasyApache 4* interface (*WHM » Home » Software » EasyApache 4*). This profile provides the *cPanel Default* profile plus the necessary packages to run NGINX.

If the `ea-nginx-standalone` package exists on your server, the system will prompt you to install NGINX with reverse proxy caching. Click *Switch to NGINX Reverse Proxy Mode* to install the package.

The system will install NGINX on your server and display a progress log. The installation process also configures all accounts on the server to use NGINX and to use caching by default.

When the installation completes, click _Go to NGINX Manager_ to return to the interface and open the _System Settings_ tab.

---

## System Settings

Use this section of the interface to manage your NGINX server. You can perform the following actions:

* *Use Caching by Default* — When you set this toggle to *Enabled*, any new accounts that you create on the server will use caching by default. This setting also applies to any accounts which do not have their caching status explicitly set.

  **Note:** When you enable or disable the caching status for a user account, the system default setting will **no longer** apply.

* *Clear Cache for All Users* — Clear the cache for all users on the system.
* *Restart NGINX* — Restart NGINX on your server.
* *Rebuild Configuration* — Rebuild the NGINX service's configuration.
* *Reset Users to System Default* — Reset all users on the system to the system's default NGINX configuration.
* *Uninstall NGINX Reverse Proxy* — Uninstall NGINX from your server.

---

## User Settings

Use this section of the interface to manage your users' NGINX settings. This section displays a table with the user's username and their NGINX caching status.

* To search for a specific user, use the *Search for account or owner* text box.
* To change a user's NGINX caching status, set the toggle next to the user's username to either *Enabled* or *Disabled*.
* To change the NGINX caching status for multiple users, select the checkbox next to the usernames you wish to change or select the checkbox above the table to select all visible users. Then, click *Enable NGINX Cache* or *Disable NGINX Cache*.
* To clear a user's cache, click *Clear Cache* next to the user's username.
* To clear the cache for multiple users, select the checkbox next to the usernames you wish to clear or select the checkbox above the table to select all visible users. Then, click *Clear NGINX Cache*.

**Note:** If you want to allow your users to manage their own NGINX caching status, enable the *EA4 - Allow enabling/disabling NGINX caching (requires cPanel & WHM version 100 or later)* option in WHM's *Feature Manager* interface (*WHM » Home » Packages » Feature Manager*). This option enables the *NGINX Caching* toggle in the cPanel interface.

---

## Uninstall

To uninstall NGINX, use the *Uninstall NGINX Reverse Proxy* option in the [System Settings](#system-settings) tab.

You can also run the following command on the command line as the `root` user:

| Operating System | Command |
| --- | --- |
| CentOS 7 | `yum uninstall ea-nginx` |
| AlmaLinux OS and Rocky Linux™ | `dnf uninstall ea-nginx` |
| Ubuntu® | `apt purge ea-nginx` |

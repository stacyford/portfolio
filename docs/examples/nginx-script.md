---
title: The ea-nginx script
---

### Overview

The `/usr/local/cpanel/scripts/ea-nginx` script manages your NGINX configuration. This script will configure or remove an NGINX user, reload the user configuration, and manage the cache. 

This script creates the user’s configuration file in the following location:

**Note**: In the following example, username represents the username.

```
/etc/nginx/conf.d/users/username.conf 
```

### Run the script

To use this script, run the following command as the `root` user:

```
/usr/local/cpanel/scripts/ea-nginx [options]
```

This script's available options change, depending on how you use the script. For more information, read the [Options](#options) section below.

### Options

This script accepts the following options, depending on the action required:

**Note**: In the following tables, user represents the cPanel username.

#### Configure NGINX users

To configure a user for NGINX, run the following command:

```
/usr/local/cpanel/scripts/ea-nginx config  [options]
```

You can use the following options with this script:

| Options | Description | Example |
| ----- | ----- | ----- |
| `user` | Configure a specific cPanel account username for NGINX. <br><strong>Note:</strong><ul><li>You **must** pass either the `user` or `--all` option, but not both.</li><li>This option also clears the user's cache.</li></ul> | `config user` |
| `--all` | Configure all cPanel accounts for NGINX. <br><strong>Note:</strong><ul><li>You **must** pass either the `user` or `--all` option, but not both.</li><li>This option builds the user configurations in parallel.</li><li>To configure the `--all` option to **always** build the user configuration serially, create the `/etc/nginx/ea-nginx/serial_config_mode` touch file.</li></ul> | `config --all` |
| `--no-reload` | Do not immediately reload the user’s NGINX configuration.  <br><strong>Note:</strong><ul><li>You can **only** use this option with the `config` or `remove` options.</li><li>You **must** pass the [`reload`](#additional-options) option by itself when you're ready to load the changes into your NGINX configuration.</li></ul> | `config user --no-reload` |
| `--serial` |  | | 

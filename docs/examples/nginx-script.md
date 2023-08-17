---
title: The ea-nginx script
---

### Overview

The `/usr/local/cpanel/scripts/ea-nginx` script manages your NGINX configuration. This script will configure or remove an NGINX user, reload the user configuration, and manage the cache. 

This script creates the user’s configuration file in the following location:

**Note**: In the following example, `username` represents the username.

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

**Note**: In the following tables, `user` represents the cPanel username.

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
| `--serial` | Rebuild the user configurations serially rather than in parallel. <br>**Note**: You can **only** use this option with the `--all` option.| `config --all --serial` |
| `--global` | Only rebuild global NGINX configurations. This option also executes any scripts in the `/etc/nginx/ea-nginx/config-scripts/global/` directory. | `config --global` |  

#### Remove NGINX users

To remove a user from NGINX, run the following command:

```
/usr/local/cpanel/scripts/ea-nginx remove  [options]
```

You can use the following options with this script:

| <div style="width:100px">Options</div>       | Description | Example |
|:----------- |:----------- |:------- |
| `user` | Remove a user from your NGINX configuration. |  `remove user` |
| `--no-reload` | Do not immediately reload the user's NGINX configuration. <br>**Note:** <ul><li>You can **only** use this option with the `config` or `remove` options.</li><li>You **must** pass the [`reload`](#additional-options) option by itself when you're ready to load the changes into your NGINX configuration.</li></ul>  |  `config user --no-reload` |

#### Configure a user NGINX cache

To configure a cPanel user's NGINX caching, run the following command:

```bash
/usr/local/cpanel/scripts/ea-nginx cache user [options]
```

You can use the following options with this script :

| <div style="width:125px">Options</div>       | Description | <div style="width:125px">Example</div> |
|:----------- |:----------- |:------- |
| `--reset`   | Remove a specific cPanel user's cache configuration and use the system's configuration. **Note**: You **must** pass either the `--reset` or `--enabled` option, but not both. | `--reset` |
| `--enabled` | Enable or disable the cPanel user's cache. You can set the following values: <ul><li> `1` — Enable the user's cache. </li><li>`0` — Disable the user's cache.</li></ul> <strong>Note</strong>: <ul><li>You **must** pass either the `--reset` or `--enabled` option, but not both.</li><li>This option also clears the user's cache.</li><ul> | `--enabled=1` |
| `--no-rebuild` | Do not reload NGINX immediately or rebuild the NGINX configuration. **Note:** You **must** pass the `config` option when you're ready to rebuild the changes to your NGINX configuration. | `--no-rebuild` |
  
#### Configure the system NGINX cache

To configure the system's NGINX caching, run the following command:

```
/usr/local/cpanel/scripts/ea-nginx cache --system [options]
```

You can use the following options with this script:

| <div style="width:125px">Options</div>       | Description | <div style="width:125px">Example</div> |
|:----------- |:----------- |:------- |
| `--reset`   | Sets the system's configuration to default values. <br>**Note:** You **must** pass either the `--reset` or `--enabled` option, but not both. | `--reset` |
| `--enabled` | Enable or disable the system's cache. You can set the following values: <ul><li> `1` — Enable the system's cache. </li><li>`0` — Disable the system's cache.</li></ul> <br>**Note**: You **must** pass either the `--reset` or `--enabled` option, but not both.| `--enabled=1`       |
| `--no-rebuild` | Do not reload NGINX immediately or rebuild the NGINX configuration. <br>**Note:** You **must** pass the `config` option when you're ready to rebuild the changes to your NGINX configuration.| `--no-rebuild` |

#### Clear the NGINX cache

To clear a user's  NGINX cache, run the following command:

```
/usr/local/cpanel/scripts/ea-nginx clear_cache [options]
```

You can use the following options with this script:

| <div style="width:100px">Options</div>       | Description | Example |
|:----------- |:----------- |:------- |
| `user`  | Clear the NGINX cache for one or more users. <br>**Note:** You **must** pass either the `user` or `--all` option, but not both.| `clear_cache user1 user2` |
| `--all` | Clear the NGINX cache for all users on the system. | `clear_cache --all` |

#### Additional options

To perform additional actions with this script, run the following command:

```
/usr/local/cpanel/scripts/ea-nginx  [option]
```

You can also use the following options with this script:

| <div style="width:150px">Options</div>     | Description     | <div style="width:125px">Example</div>  |
| :------------ | :------------ | :------------ |
| `help [option]` | Display the script's help information. <br>**Note:** If you specify an option, **only** that option's help information will appear.| 	`help reload` |
| `hint [option]` | Display the abbreviated help information. <br>**Note:**If you specify an option, **only** that option's hint information will display. | `hint reload`|
| `reload` | Reload your NGINX configuration.<br>**Note:**<ul><li>You **must** pass this option if you passed the `--no-reload` option when configuring the NGINX system or users.</li><li>This option also clears the user's cache.</li><ul>| `reload` |


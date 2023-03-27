---
title: Package Manager Basics
---


### Overview

Package managers allow you to easily update, install, and remove software packages on your system. Package managers use repositories to manage the packages that you install or uninstall. They  also handle any dependencies for packages that you wish to use. If you set your package manager to automatically update your system's packages, you will not need  to run the updates manually.

You can configure your system's update schedule in WHM's Update Preferences interface.

Different operating systems support different package managers. In a CentOS-based system, you use <a href="http://yum.baseurl.org/" target="_blank">yum</a> to manage your packages. In an Ubuntu-based system, you use <a href="https://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html" target="_blank">apt</a> to manage your packages.

### What is a  repository?

A repository is a collection of packages on your local machine or one that you can access remotely via FTP or HTTP. You can use several repositories at the same time.

#### CentOS repositories

CentOS uses yum to manage the packages in its repositories.

The following preconfigured repositories exist on CentOS systems:

* `base`
* `updates`
* `extras`
* `centosplus`
* `fastrack`

The system stores yum repositories in the `/etc/yum.repos.d/` directory. Usually, each repository owns its own file. Each file can contain one or more configuration blocks that define the available yum repositories. These files ensure that yum allows the software that third parties provide. You do **not** need to edit them.

To access a new repository, download the `.repo` file from the desired third party to the `/etc/yum.repos.d/` directory and then run the `yum update` command.


#### Ubuntu repositories

Ubuntu uses apt to manage the  packages in its repositories.

The following preconfigured repositories exist on Ubuntu systems:

* `Main`
* `Universe`
* `Multiverse`
* `Restricted`
* `Partner`

The system stores its preconfigured repositories in the `/etc/apt/sources.list` file. Usually, each repository owns its own file. Each file can contain one or more configuration blocks that define the available apt repositories. These files ensure that apt allows the software that third parties provide. You do **not** need to edit them.

To access any other repositories, download the `.list` file  to the `/etc/apt/sources.list.d/` directory and then run the `apt update` command.

### Package management in EasyApache 4

cPanel & WHM ensures that installed packages **do not** conflict with one another. The cPanel & WHM-provided packages in the EasyApache 4 repositories use the `ea-` prefix, or namespace. EasyApache 4 provides packages in both RPM and `.deb` format.

#### Manage packages on CentOS systems

To manage packages on a CentOS system, use the `yum` command.

**Note:**
In the following table, `example` represents the name of the package that you wish to install.


|Command| Description|
|-----|-----|
| `yum install example` |  Install the `example` package from a repository to your system.|
| `yum erase example` or `yum remove example`| Uninstall the `example` package and any dependencies.|
| `yum update` |  Update all of the packages on your system.|
| `yum update example` | Update the `example` package on your system.|
| `yum upgrade` | Upgrade the packages on your system.{{% callout type="info" header="Note:"%}}This command also removes any obsolete packages on your system.{{% /callout %}}|

For more information about yum, read the <a href="http://yum.baseurl.org/wiki/YumCommands.html" target="_blank">yum documentation</a>.

#### Manage packages on Ubuntu systems

To manage packages on an Ubuntu system, use the `apt` command.

**Note:**
In the following table, `example` represents the name of the package that you wish to install.


|Command| Description|
|-----|-----|
| `apt install --purge example` |  Install the `example` package from a repository to your system.|
| `apt purge example`| Uninstall the `example` package, all configuration files, and any dependencies.|
| `apt update` |  Download the package information from all configured repositories.|
| `apt upgrade --purge` | Install any available upgrades for packages on your system.|

The `--purge` option ensures that the system removes any unneeded package dependencies and any non-binary files that the package owns. If you run the `install` or `upgrade` commands **without** the `--purge` option, then apt will **not** remove these files, and errors may occur.

For more information about apt, read the <a href="https://manpages.ubuntu.com/manpages/xenial/man8/apt.8.html" target="_blank">apt documentation</a>.

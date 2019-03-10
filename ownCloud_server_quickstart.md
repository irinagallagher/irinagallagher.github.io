---
layout: post
permalink: /admin/
---

# Owncloud Server Quickstart Guide
This guide is aimed at helping **Administrators** get an ownCloud Server up and running in a production environment, using the **ownCloud tarball** installation option.

The following installation options are also available, and further details on how to use these options can be found at the link provided:

* [Installing with Docker](https://doc.owncloud.org/server/10.1/admin_manual/installation/docker/)
* [Ready-to-deploy package](https://download.owncloud.org/download/repositories/stable/owncloud/index.html) for the following Linux distributions: CentOS, Debian, Fedora, openSUSE, SLE, Ubuntu, RHEL.

> **Note**: The Appliance installation is recommended for non-technical users - see [here](https://doc.owncloud.org/server/10.1/admin_manual/appliance/installation.html) for details.

## Download the ownCloud Server
1. Download the latest production release tarball from [https://owncloud.org/download/](https://owncloud.org/download/).
2. Verify the PGP signature:

    ```
    wget https://download.owncloud.org/community/owncloud-x.y.z.tar.bz2.asc
    wget https://owncloud.org/owncloud.asc
    gpg --import owncloud.asc
    gpg --verify owncloud-x.y.z.tar.bz2.asc owncloud-x.y.z.tar.bz2
    ```
3. Install, enable and configure the required PHP extensions - see [Prerequisites](https://doc.owncloud.org/server/10.1/admin_manual/installation/manual_installation.html#prerequisites) for a complete list and further details.

## Install the ownCloud Server
1. Extract the tarball to the required location. The tarball unpacks into a directory named `owncloud`.
2. Configure the Apache Web Server - see [here](https://doc.owncloud.org/server/10.1/admin_manual/installation/manual_installation.html#configure-the-web-server) for details.
3. Complete the installation using either the [Graphical Installation Wizard](https://doc.owncloud.org/server/10.1/admin_manual/installation/installation_wizard.html) or the [command line](https://doc.owncloud.org/server/10.1/admin_manual/installation/command_line_installation.html).
4. Set directory permissions using the guidance provided [here](https://doc.owncloud.org/server/10.1/admin_manual/installation/installation_wizard.html#post-installation-steps).
5. Install the relational database your ownCloud Server will use.

## Enable Users to Connect to ownCloud
To enable users to connect to ownCloud you need to configure the ownCloud Access URLs in `config/config.php`:

1. Add the ownCloud Server domain name to the `trusted_domains` section of `config/config.php`:
  ```
  'trusted_domains' => [
     0 => 'localhost',
     1 => 'server1.example.com',
     2 => '192.168.1.50',
  ],
  ```
2. Add any additional URLs that can be used to log into ownCloud to the `trusted_domains`.

You are now ready to start fine tuning the configuration of the ownCloud Server to your requirements. See [Server Configuration]( https://doc.owncloud.org/server/10.1/admin_manual/configuration/server/activity_configuration.html) for details on the features and functions that can be configured.

## Add User Accounts
User accounts are added and managed using the ownCloud Web UI:

<img src="https://doc.owncloud.org/server/10.1/admin_manual/_images/docker/owncloud-ui-login.png" alt="ownCloud Web UI" width="600"/>

1. Login to the ownCloud Web UI using the Administrator account by entering the server address, [http://localhost:8080](http://localhost:8080), in a browser.
2. Open the User management page.

   <img src="https://doc.owncloud.org/server/10.1/admin_manual/_images/users-config.png" alt="ownCloud Web UI User Mgmt Page" width="600"/>

3. (Optional) Ensure the "Send email to new user" option is selected in the settings - open the Settings screen by selecting the gear icon:

   <img src="https://doc.owncloud.org/server/10.1/admin_manual/_images/users-config-2.png" alt="ownCloud Web UI Settings" width="200"/>
4. Enter the username and an initial password for the new user in the Username and Password fields.
5. (Optional) Select the group(s) the user belongs to from the drop-down `Groups` field.
6. Select `Create`. The new user will be sent an email if the "Send email to new user" setting has been selected.

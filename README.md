![banner](https://cloud.githubusercontent.com/assets/7253840/26084852/93c67d0a-399c-11e7-8370-45bd51bb8003.png)

# About

Private, easy to use, file manager plugin for OctoberCMS that provides access to authenticated users only. Based on the built-in Media Manager, this plugin is easy to use and configure to your needs. Great for your business file management needs; from sharing internal documents among authorized users to integrating with your existing file storage system to provide a seamless experience managing your files from within your OctoberCMS-power site.

# Installation

To install from the [Marketplace](https://octobercms.com/plugin/luketowers-filelocker), click on the "Add to Project" button and then select the project you wish to add it to before updating the project to pull in the plugin.

To install from the backend, go to **Settings -> Updates & Plugins -> Install Plugins** and then search for `LukeTowers.FileLocker`.

# Usage

After installing the plugin, you will need to grant permissions to the users / groups that you want to use this plugin. In order to grant the following permissions to a user group, go to **Settings -> Administrators -> Manage Groups** and select the group you want to grant permissions for this plugin to. Scroll down the Permissions list until you see the "FileLocker" section. The following permissions and their effects are explained below:

Permission | Effect
------------- | -------------
**Manage Plugin Settings** |  Manage the FileLocker plugin's settings. (Currently only the ability to change the name of the File Locker menu item)
**Download Files** | Download any file from the FileLocker, provided they have a URL to the file. Used for people that you want to be able to have access to download the files, but not to view all of them or upload new files.
**Manage all files** | Manage (add, view, update, or delete) any file in the FileLocker

# Advanced Configuration

At present time, any advanced configuration is handled by overriding this plugin's configuration and changing the necessary values by copying **config/config.php** from the plugin into your project's **config/luketowers/filelocker/config.php** file [(as specified in the OctoberCMS docs)](http://octobercms.com/docs/plugin/settings#file-configuration). The following config values are [documented on Github](https://github.com/LukeTowers/oc-filelocker-plugin/blob/master/config/config.php):

Configuration Key | Effect
------------- | -------------
**storage.disk** |  The storage disk (as defined in the `filesystems::disks` config - **config/filesystems.php**) to use for storing and retrieving files from. Any disk using any driver supported by Laravel is supported here. Check the [storage disks](#storage-disks) section to see the possibilities here.
**storage.folder** | The folder on the storage disk to use for storing and retrieving files.
**storage.path** | The URL path to access files directly under. By default it is **yourdomain.com/luketowers.securefiles/download/$pathToFileHere** but you can change this value to make it anything you want; i.e. perhaps **yourdomain.com/boardfiles/download/$pathToFileHere**. The only restriction is that the URL must be able to be handled by the October instance that this plugin is installed on, it can't respond to download requests if the code to do so isn't present on that server.
**manager_title** | The title of the File Locker menu item. Language keys are acceptable here as well as just plain ordinary strings of test.

> *NOTE*: **manager_title** is manageable by visiting the **FileLocker** settings page in the backend by a user with the **manage_settings** permission.

![Settings page screenshot](https://cloud.githubusercontent.com/assets/7253840/26083754/bb065de8-3994-11e7-88b9-b5dbc8a32466.png)

<a name="storage-disks"></a>
# Storage Disks

As stated above, this plugin supports any storage disk / driver that Laravel supports. This includes built in disks / drivers like `local` or `ftp` but also includes custom drivers like [SFTP](https://github.com/thephpleague/flysystem-sftp), [AWS S3](http://octobercms.com/plugin/october-drivers), [Rackspace](http://octobercms.com/plugin/october-drivers), [Microsoft Azure Blob Storage](http://octobercms.com/plugin/pvaass-azurefiledriver) and even [Google Drive](https://gist.github.com/ivanvermeyen/cc7c59c185daad9d4e7cb8c661d7b89b)

> **NOTE**: These drivers need to be installed and configured separately before they can be used for this plugin, but a planned feature for the future is the ability to setup these drivers through the Backend FileLocker Settings page. If you would like to see that feature sooner rather than later, shoot me an email at octobercms@luketowers.ca

# Reporting Issues

If you find a bug in this plugin, or would like a feature added, please use the [public repository's Issues section](https://github.com/LukeTowers/oc-filelocker-plugin-issues/issues). If you find a security vulnerability or have an urgent issue that needs to be addressed, please contact me directly at octobercms@luketowers.ca.

Roundcube Gravatar
==================

Non official plug-in showing [Gravatar](https://www.gravatar.com/) profile images inside the [Roundcube webmail](https://roundcube.net/) client.

It has been implemented as Roundcube readonly hidden addressbook. You have to ensure this plugin is added into the latest entry in the main config (`$config['plugins']`). If so and any address book (LDAP, Google, etc...) already has a photo for a contact it will use first the other pictures and lastly if none reported it will use gravatar (Roundcube will use it in following the order listed in the main config).

Tested in roundcube 1.2.0.

Installation
============

Intallation steps:
  - Via composer:
    - Run `php composer.phar require prodrigestivill/gravatar`.
  - Via git:
    - Clone the repository:
      `cd roundcube/plugins && git clone git@github.com:prodrigestivill/roundcube-gravatar.git gravatar`
  - Via tarball:
    - Download and extract the tarball into `roundcube/plugins` directory and rename the extracted directory to `gravatar`.

For the expected behaviour ensure it is always the latest plugin (or at least addressbook plugin) in the `$config['plugins']` list at `config/config.inc.php`.

To enable per user: Login to Roundcube and enable/disable plugin by navigating to the Settings page, clicking on Preferences, click on Address Book, and Enable Gravatar, and Save.

To configure/change default values:
  - Copy `config.inc.php.dist` to `config.inc.php` in `plugins/gravatar/` directory.
  - Modify the values you are interested into change and comment the rest with '//'

Custom API
==========

You can define your custom API for photos at 'gravatar_photo_api' in `config.inc.php`.
  - %%: literal '%'
  - %s: schema ('http', 'https') depending of 'gravatar_https' config
  - %h: server host defined in 'gravatar_server' config
  - %e: contact email
  - %m: md5(email)
  - %a: sha1(email)
  - %z: configured avatar size (in px)
  - %r: configured rating ('g', 'pg', 'r', 'x')

As an example, default gravatar api is: '%s://%h/avatar/%m?s=%z&r=%r&d=404'

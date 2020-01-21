# Accessing the server

- Each adminstrator has to create his/her own account and ask one of the existing adminstators for being added to `lgm` group
- then you can connect yourself to `ssh.tuxfamily.org`
- if you get a notice saying "This is a disabled shell account.", you need to log into http://tuxfamily.org, go into your account settings, and select the Shell type that fits your needs.
- if you upload your `id_rsa.pub` as `~/ssh_keys` and set its permissions to `400`, you will be able to login by using your private key.

# The website

- `lgm/` contains the wordpress instance for the general information on the LGM
- `2007/`-`2015/` contains the site for each year's LGM (the last one as a wordpress instance, the other ones as static html)

Setup a new wordpress instance:

- go to the `htdocs/` folder
- `wget` inside of it the newest wordpress and unpack it
- `rename the new `wordpress/` directory as `20xx` (where xx is the year for the instance)
- browse to `http://libregraphicsmeeting.org/20xx` and install wordpress, using the `lgm_20xx`database and with the `wpxx_` prefix for the tables (look for the access data in an older `wp-config.php` file
- [move the wordpress files in its own `wp/` directory](https://codex.wordpress.org/Giving_WordPress_Its_Own_Directory#Method_II_.28With_URL_change.29)
- in the general settings, set the tagline
- create a github repository for the theme.
- install the usual plugins:
  - LGM Sanitize Settings 2017
  - WP Libre Form
- copy over the forms
- define the usual sidebar widgets

## The databases

- `lgm_lgm` for the `lgm/` wordpress.
- `lgm_20xx` for the current year's wordpress.
- the username is the same as the name of the database
- you'll find the password in the older `wp-config.php` files.
- the address to the database is `sql` instead of `localhost` entrer: sql
- more info: <http://faq.tuxfamily.org/DbMySQL/En>

## The download / static files area

Here is the official how-to by tuxfamily:

- https://faq.tuxfamily.org/Downloads/Fr
- https://faq.tuxfamily.org/Downloads/En

The shorter version:

- You need a tuxfamily (panel) account to be able to upload files
- You can upload files with sftp (username@ftp.tuxfamily.org) or wget them from your ssh session.

## PHP and log errors

By default, errors are not shown.

- put `phpinfo()` in a file to discover which one is the current active `php.ini`
- copy the current `php.ini` to your current directory

  ```
  cp /etc/php/7.3/cli/php.ini .
  ```
- add the line activating the error_log

  ```
  error_log = "${DOCUMENT_ROOT}/../php-include/2020/logs/php_errors.log"
  ```

  `php-include` is the only place outside of `htdocs` where you are allowed to write from php. create a directory with year in there, with a logs directory.
- write a script that can show the content of the `php_errors.log` (you can make it world readable or add a (weak) password to it):

  ```
  <?php
  $path_to_logs = dirname($_SERVER['DOCUMENT_ROOT']).'/php-include/2020/logs';
  ?>
  <!DOCTYPE html>
  <html lang="en">
    <head>
      <meta charset="utf-8">
      <title>php errors</title>
    </head>
    <body>
      <pre>
      <?= file_get_contents($path_to_logs.'/php_errors.log'); ?>
      </pre>
    </body>
  </html>
  ```
- don't forget  remove the custom `php.ini` when you're done with the debugging (otherwise there might be issues when php is upgraded).

You can also put a password file in the logs directory and use it to protect the logs:

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>title</title>
    <link rel="stylesheet" href="style.css">
    <script src="script.js"></script>
  </head>
  <body>
<?php
$path_to_logs = dirname($_SERVER['DOCUMENT_ROOT']).'/php-include/2020/logs';
?>
<?php if (array_key_exists('password', $_POST) && $_POST['password'] == trim(file_get_contents($path_to_logs.'/password-secret'))) : ?>
<pre>
<?php
echo(file_get_contents($path_to_logs.'/php_errors.log'));
?>
</pre>
<?php else: ?>
<form method="post">
<input type="password" name="password">
<input type="submit" value="go">
</form>
<?php endif; ?>
  </body>
</html>
```

## How to get support

- go to the irc channel
- send an email to `modo at staff dot tuxfamily dot org`


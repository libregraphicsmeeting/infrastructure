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

## The databases

- `lgm_lgm` for the `lgm/` wordpress.
- `lgm_20xx` for the current year's wordpress.
- the username is the same as the name of the database
- you'll find the password in the older `wp-config.php` files.
- the address to the database is `sql` instead of `localhost` entrer: sql
- more info: <http://faq.tuxfamily.org/DbMySQL/En>

# How to get support

- go to the irc channel
- send an email to `modo at staff dot tuxfamily dot org`

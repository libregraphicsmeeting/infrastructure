# Accessing the server

- Each adminstrator has to create his/her own account and ask one of the existing adminstators for being added to `lgm` group
- then you can connect yourself to `ssh.tuxfamily.org`
- if you get a notice saying "This is a disabled shell account.", you need to log into tuxfamily.org, go into your account settings, and select the Shell type that fits your needs.

# The website

- `lgm/` contains the wordpress instance for the general information on the LGM
- `2007/`-`2015/` contains the site for each year's LGM (the last one as a wordpress instance, the other ones as static html)

## The databases

- `lgm_lgm` for the `lgm/` wordpress.
- `lgm_20xx` for the current year's wordpress.
- the username is the same as the name of the database
- the address to the database is `sql` instead of `localhost` entrer: sql
- more info: <http://faq.tuxfamily.org/DbMySQL/En>

# How to get support

- go to the irc channel
- send an email to `modo at staff dot tuxfamily dot org`

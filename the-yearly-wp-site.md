# Create the yearly Wordpress instance

## Setup the Github repository

- create a new Github repository with the name `htdocs-YYYY`
- create the `wp/wp-content/themes/lgmYYYY/` directory with a `README.md` file
- give write access to the web persons in the local team 
- setup the web hook that triggers the syncing php script on the tuxfamily server.

## Setup Wordpress

The infrastructure group sets up the Wordpress instance.

## Create the yearly theme

Normally, the local team is in charge of the look and content of the website:

- Locally install Wordpress and [move the instance into a `wp/` directory](https://codex.wordpress.org/Giving_WordPress_Its_Own_Directory#Method_II_.28With_URL_change.29)
- Get the stub for the yearly team from the LGM Github repository.
- Create the new theme in the `wp/wp-content/themes/lgmYYYY/` directory.
  - You can create it as a child of an existing theme.
- Push it to the Github repository when it's ready. It will be automatically deployed on the live server.
  - Don't put any file outside of the `lgmYYYY? theme directory.

## Archive the site as a static site

After the LGM, we normally remove Wordpress and make the site static.

```wget -r -np  http://

### Troubleshooting

- finding big directories:  
  `du -h --max-depth=1`
- finding big files:  
  `ls -lhS`
- if the links to the css and js are over http:  
  `find . -type f -name "*.html" -exec sed -i 's/http:/https:/g' {} +`
- if there are files ending in php:  
  `rename 's/\.php/.html/' *.php`  
  and add a `.htaccess` file:

  ```
    RewriteEngine on
    RewriteCond %{THE_REQUEST} \ /(.+)\.php
    RewriteRule ^ /%1.html [L,R=301] 
  ```
- wget creates js and css files with `?ver=...` at the end... just rename the files and remove the version.

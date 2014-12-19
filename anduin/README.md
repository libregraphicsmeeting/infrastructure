the old libregraphicsmeeting website was provided by anduin.net and managed by the scribus team (mostly mrdocs, peter linnell)

the server can still be reached by http and ssh through its ip address: 31.185.27.103

if you'd like to access old instances of wordpress on the server, you should temporarly redirect the libregraphicsmeeting.org domain to that ip address:

- on linux and os x you can edit the `/etc/hosts` file and add the following line:

      31.185.27.103   libregraphicsmeeting.org

- open an ingognito window -- to avoid cached routes -- and go to <http://libregraphicsmeeting.org/2014/wp/wp-admin/>
- close the window and delete the `/etc/hosts` entry when you're done.

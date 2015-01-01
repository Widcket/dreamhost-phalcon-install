#Installing Phalcon on a shared Dreamhost server
Here's a way to install the [Phalcon PHP framework](http://phalconphp.com/) on a shared DH account by using a precompiled, DH-tailored Phalcon build. I will assume you know how to access the server via ssh and how to use basic terminal.

##Requirements
1. A shared Dreamhost account with shell access
2. A domain running PHP 5.6.x w/ FastCGI. The Phalcon builds I'm providing won't work with older versions of PHP, so in that case you'll need to upgrade  or [compile phalcon.so](http://serverfault.com/questions/607104/how-can-i-install-phalcon-or-any-custom-php-module-extension-on-my-shared-cpan/607105) yourself.

##Steps
1. Login to your account via ssh
2. Make sure you're in the home directory

	```$ cd ~/```
3. Create a folder to put Phalcon into

	```$ mkdir extensions```
4. Grab Phalcon. Replace `__PHALCON_VERSION__` with the one you want, e.g. `2.0.0b3`

	```wget -O extensions/phalcon.so https://github.com/Widcket/dreamhost-phalcon-install/blob/master/__PHALCON_VERSION__/phalcon.so?raw=true```
5. Create a folder to put the phprc file into 

	```$ mkdir -p .php/5.6```
6. Create the phprc file

	```$ nano .php/5.6/phprc```
7. Drop this line in. Replace `__USERNAME__` with your actual username

	```extension = /home/__USERNAME__/extensions/phalcon.so```
8. Save the file and exit (Ctrl+O then Ctrl+X)
9. You're done! Check it with `phpinfo()`.
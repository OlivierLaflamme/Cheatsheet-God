# Enabling Self signed certificates on local website
    
1. Install OpenSSL

sudo apt-get install openssl

2. Run the following command to generate the self signed SSL certificates:

sudo openssl req -x509 -nodes -days 1095 -newkey rsa:2048 -out /etc/ssl/certs/server.crt -keyout /etc/ssl/private/server.key

3. Enable SSL for Apache

sudo a2enmod ssl

4. Put the default-ssl site available creating a symbolic link

sudo ln -s /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/000-default-ssl.conf

5. Edit the file default-ssl.conf

sudo nano /etc/apache2/sites-enabled/000-default-ssl.conf

Change the following lines to point to the certs:

SSLCertificateFile    /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key

6. Restart Apache

sudo /etc/init.d/apache2 restart

More information:
https://hallard.me/enable-ssl-for-apache-server-in-5-minutes/
https://www.sslshopper.com/article-how-to-create-and-install-an-apache-self-signed-certificate.html
http://www.akadia.com/services/ssh_test_certificate.html
https://www.sslshopper.com/apache-server-ssl-installation-instructions.html
http://www.emreakkas.com/linux-tips/invalid-command-sslengine-enabling-ssl-on-ubuntu-server
# install-apache-server

How to install apache server.
> This is the easy way to install  **Apache server**.
1. You need to know what the developer or you need.
2. I just need apache and phpmyadmin and git & php

**Lets start**
> First update your system apt

```sudo apt-get update```

Then
> Add the php repository on your source list
___

```sudo apt install apt-transport-https lsb-release ca-certificates```
___
```wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg```
___
```echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" >> /etc/apt/sources.list```
___
Then 
```sudo apt update```

Now , install the php and dependencies.

```sudo apt-get install php7.4 php7.4-curl php7.4-gd php7.4-json php7.4-mbstring php7.4-intl php7.4-mysql php7.4-xml php7.4-zip```
___
Install Mysql-server

```sudo apt install mysql-server```
___
Then install php-myadmin

```sudo apt-get install phpmyadmin```
___
**Created a symlink for phpmyadmin**

```cd /var/www/html/

sudo ln -s /usr/share/phpmyadmin```

If you need git install it

```sudo apt-get install git```
___
Its time to configure
You need to know that the apache sites-availables configuration is locate here */etc/apache2/sites-available*

Create your file configuration , */etc/apache2/sites-available/your.conf*

Edit your file configuration  with your best editor

```nano /etc/apache2/sites-available/your.conf```

*Add this line*

```
NameVirtualHost Your server-ip-adress or your domain.name
        <VirtualHost your ip adress:80>
        DocumentRoot /you/directory
        <Directory /you/directory>
                Order allow,deny
                Allow from all 
        </Directory>
</VirtualHost>
```

You need to ensite your configuration

```a2ensite your.conf```

Deactivates a default configuration file 00-default.conf

```a2dissite 00-default.conf```

**Restart apache**

```service apache2 restart```

Edit your apache configuration

*edit /etc/apache2/apache2.conf with your editor and set AllowOverride None to All , **This is important** *

```a2enmod rewrite```

Restart your web server

```sudo service apache2 restart```

no open the browser

http://your_ip

```
Problème mpahazo 
in ./libraries/sql.lib.php#613
 count(): Parameter must be an array or an object that implements Countable
 
 **Solutions**
 ```sudo sed -i "s/|\s*\((count(\$analyzed_sql_results\['select_expr'\]\)/| (\1)/g" /usr/share/phpmyadmin/libraries/sql.lib.php```
 
  in ./libraries/plugin_interface.lib.php#551
 count(): Parameter must be an array or an object that implements Countable
 
 ```if ($options != null && count((array)$options) > 0) {``` ligne 532

**Happy hacking**







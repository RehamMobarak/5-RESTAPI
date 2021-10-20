Simple Api tutorial

First make sure that composer,git,php are installed and working properly 

To Clone/download repository to your local machine, run command:

$ git clone https://github.com/RehamMobarak/5-RESTAPI.git

Go to the folder containing the project ( for Ubuntu use cd PROJECTPATH)

Run composer install on your cmd or terminal to download the required packages for the projects to run.

Open your .env file and change the database name (DB_DATABASE) to whatever you have, username (DB_USERNAME) and password (DB_PASSWORD) field correspond to your configuration.
    By default, the username is root and you can leave the password field empty. (This is for Xampp)
    By default, the username is root and password is also root. (This is for Lamp)

Run php artisan key:generate

Run php artisan migrate

To run the project:
    Run php artisan serve

    Go to localhost:8000
OR:

make a virtual host on your machine to run the project using a url
For ubuntu:

(1) go to /etc/apache2/sites-available folder.

(2) Copy 000-default.conf file or create a new file at that location with the name of the domain you want, i.e., test.site.conf -- itemapi.stg.conf.

(3) put that code with changes according to the project name and location:

<VirtualHost *:80>
    ServerAdmin admin@domain.com
    ServerName itemapi.stg  //custom 
    ServerAlias itemapi.stg //custom
<Directory project-path>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
</Directory>
    DocumentRoot project-path/public
    ErrorLog project-path/error.log
    CustomLog project-path/access.log combined
</VirtualHost>


(4) Now you need to tell apache that this conf file ready to be served, so you need to run this command:
sudo a2ensite test.site.conf

sudo service apache2 restart

(5) to solve permission problem make sure there is no VPN running and you may need to run these commands:
sudo a2enmod rewrite
sudo service apache2 restart

-- if not working got to project and run:
php artisan config:clear
php artisan cache:clear
sudo chmod -R 775 project-path (proj loaction)
sudo chown -R www-data:www-data project-path (proj loaction)

(6) to register the new DNS, go /etc/hosts file and put an IP and DonmainName:
127.0.0.1  itemapi.stg

restart apache sudo service apache2 restart
and test it!


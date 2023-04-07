# OpenProject
This is just an Installation guide of OpenProject in Ubuntu/debian.

## How to install OpenProject on Ubuntu 20.04


Adding OpenProject Repository & Installation.
Well, the open project repo is not included in Ubuntu by default so, we need to manually add the repo to our default repo list and install it. Before adding the repo we need to add a PGP key to verify the signature of the package. To add the key execute the following command.

    $ wget -qO- https://dl.packager.io/srv/opf/openproject/key | sudo apt-key add -
Add repository key

PGP Key registration.

Now, add the OpenProject repo by using the following command,

In Ubuntu 20.04 LTS

    $ sudo wget -O /etc/apt/sources.list.d/openproject.list https://dl.packager.io/srv/opf/openproject/stable/11/installer/ubuntu/20.04.repo
In Ubuntu 18.04

    $ sudo wget -O /etc/apt/sources.list.d/openproject.list https://dl.packager.io/srv/opf/openproject/stable/11/installer/ubuntu/18.04.repo
    
Once the OpenProject repo is added we can install the package using the apt command. For that run:
    $ sudo apt update
    $ sudo apt install openproject
### OpenProject Configuration
After successfully installing OpenProject, we need to configure it using the wizard that is installed along with the package. To start the wizard run:

    $ sudo openproject configure
During initial configuration, you need to choose the edition type one is the default edition which is for general project management, and another BIM that is especially for the construction industry. So, I will go with default as we will be using it for project management.

Configure OpenProject

Initial Configuration.

After the edition type is selected we need to configure the data. As the OpenProject uses Postgresql for the database, the wizard will manage the local installation of the database. If you have a configured database you can go with the existing Postgresql database. I have installed Postgresql on my system so I will go with the installation which is managed by wizard automatically.
Advertisement

# Install PostgreSQL

Postgresql database setup.

Next, you need to install and configure the apache2 web server to access OpenProject externally. If you want to manually set up the web server you can simply select skip. The OpenProject handles the web server installation as extra dialog will appear requesting domain name and SSL certificate location (optional) if you choose to install via the wizard.

![MasterHead](https://vitux.com/wp-content/uploads/word-image-63.jpeg?ezimgfmt=ng:webp/ngcb10)

### Install Apache web server

Apache2 Server setup.

In this article, I want to host locally so I will access it through my local IP address. If you have a domain you can specify the domain and continue with it.

![MasterHead](https://vitux.com/wp-content/uploads/word-image-64.jpeg?ezimgfmt=ng:webp/ngcb10)

Server Hostname

Configuring Domain.

You can specify the server path prefix where your OpenProject instance will be run for example if you set the prefix to /openproject your OpenProject will be run on your domain.com/openproject. You need to specify the prefix with the leading slash(/). If you set the prefix empty it will run on your root of the domain such as your domain.com/. Then, I want to go with the default so I will continue with the empty prefix.
Server path prefix

Server path prefix.

If you have a valid SSL certificate you can enable SSL for your OpenProject otherwise, you can simply skip it. I don’t have one so I will select no.

Enable SSL

SSL configuration.

Next, you will be asked if you want to install the subversion repository and git in succession. I will simply skip subversion and install git as I will be using it.

Add SVN support

Subversion repository setup.

Add GIT support

Git repository setup.

If you choose to install you will ask if you want to change the directory to host git repositories. If you want you can change or go with the default.

GIT repository path

Git repository path.
Again, you will be asked if you want to change the path for git HTTP backend CGI. You can go with default if you want.

GIT http backend

CGI directory path.

If you wish to set up an email sender for the open project you can choose either Sendmail or SMTP for email sending. As of now, I don’t need email sending so I simply skip it.

SMTP configuration

#### Mail server setup.

Lastly, OpenProject relies on caching so it’s better to install the local Memcached server for better performance.

Install memcached

Memcached server setup.
After you hit enter OpenProject will start the set up according to your configuration which might take some time.

OpenProject Dashboard
Once everything is set up you can browse the OpenProject homepage from where you can log in. As I have locally installed it I will be accessing it through my network IP. initially the login of the OpenProject is,

    $ Username: admin

    $ Password: admin

OpenProject dashboard

On the first login, you will be prompted to change the password of the admin login. Once you change the admin password you will be redirected to the OpenProject dashboard where you can create a project.
Change password

Conclusion
In this article, we learn how we can install OpenProject in our Ubuntu system. I hope this article helps you to set up OpenProject.

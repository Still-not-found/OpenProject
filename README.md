# OpenProject
This is just an Installation guide of OpenProject in Ubuntu/debian.
# How to install OpenProject on Ubuntu 20.04
Open Project is an open-source application for project management that is completely web-based written in Ruby on Rails and Angular js. It provides agile as well as classical management for the entire project life-cycle. Generally, the open project is distributed in three versions: community, cloud, and enterprise edition. In this article, we will install a community version of the open project that is released under the General Public License Version 3. To demonstrate the example I have used the Ubuntu 20.04 LTS system.

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

OpenProject Configuration
After successfully installing OpenProject, we need to configure it using the wizard that is installed along with the package. To start the wizard run:

$ sudo openproject configure
During initial configuration, you need to choose the edition type one is the default edition which is for general project management, and another BIM that is especially for the construction industry. So, I will go with default as we will be using it for project management.

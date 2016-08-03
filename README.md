UrbIS Docker
---------------------

**Getting Started**
 - Clone this repository
   - $ git clone .....
 - Sync the required repositories
   - $ git clone git@code-int.ornl.gov:xs7/UrbIS.git urbisnode/urbisnode
   - $ cd urbisnode/urbisnode && npm install && bower install && cd ../..
 - Install docker - there is a beta version that runs natively on windows and osx (linux is already supported).  You can also install the dockertoolkit that uses virtualbox for non-linux boxes
 - Build the containers
   - $ docker-compose build
 - Run the containers
   - $ docker-compose up

This will give you: 
 - Postgis with PostgreSQL connect to localhost:25432
 - Python Jupyterhub for python 2 and 3 use localhost:8000 (user name jupyter password jupyter)
 - UrbIS node application at localhost:3002.


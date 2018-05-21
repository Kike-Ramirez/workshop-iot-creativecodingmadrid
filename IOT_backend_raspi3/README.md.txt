* Raspberry PI 3
* Backend THINGSBOARD.IO Installation


** Preliminars

a) If not done before, update your system.
b) Check your java version is minimum 1.8.0_65, using:

'''java -version'''
c) If necessary, update java version or install it.

d) Install POSGRESQL DATABASE if preferred (thingsboard uses an internal one, but this step is recommended)

d.1) Install necessary packages and start database service:
'''
sudo apt-get install postgresql postgresql-contrib -y
sudo service postgresql start
'''

d.2) If you want to create a new user for database, check: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04#using-postgresql-roles-and-databases

d.3) Set a new PASSWORD for main user (postgres), check: https://blog.2ndquadrant.com/how-to-safely-change-the-postgres-user-password-via-psql/
'''
postgres=# \password
Enter new password:
Enter it again:
postgres=#
'''



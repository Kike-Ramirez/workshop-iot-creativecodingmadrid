# Raspberry PI 3
# Backend THINGSBOARD.IO Installation


## Preliminars

1. If not done before, update your system.
2. Check your java version is minimum 1.8.0_65, using:

`java -version`

![java version](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_backend_raspi3/images/checkJAVA.png)

3. If necessary, update java version or install it.

4. Install POSGRESQL DATABASE if preferred (thingsboard uses an internal one, but this step is recommended)

* Install necessary packages and start database service:
`sudo apt-get install postgresql postgresql-contrib -y`
`sudo service postgresql start`

* If you want to create a new user for database, check: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04#using-postgresql-roles-and-databases

* Set a new PASSWORD for main user (postgres), ideally use also "postgres" to avoid modifying setting files. Check: https://blog.2ndquadrant.com/how-to-safely-change-the-postgres-user-password-via-psql/

`sudo -i -u postgres`
`psql`
`postgres=# \password`
`Enter new password:`
`Enter it again:`
`postgres=#`

* Launch database server and connect it to Server

`psql -U postgres -d postgres -h 127.0.0.1 -W`

`CREATE DATABASE thingsboard;`
`\q`



## Thingsboard.io Server - Install & Launch

1. Download debian package

`# Download the package`
`$ wget https://github.com/thingsboard/thingsboard/releases/download/v1.4/thingsboard-1.4.deb`
`# Install ThingsBoard as a service`
`$ sudo dpkg -i thingsboard-1.4.deb`
`# Update ThingsBoard memory usage and restrict it to 150MB in /etc/thingsboard/conf/thingsboard.conf`
`export JAVA_OPTS="$JAVA_OPTS -Dplatform=rpi -Xms256M -Xmx256M" ` 

![thingsboard_setup](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_backend_raspi3/images/thingsboard_download.png)

![thingsboard_install](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_backend_raspi3/images/thingsboard_install.png)

2. Configure POSTGRES as database server

`sudo nano /etc/thingsboard/conf/thingsboard.yml`

* Comment ‘# HSQLDB DAO Configuration’ block.

`# HSQLDB DAO Configuration`
`#spring:`
`#  data:`
`#    jpa:`
`#      repositories:`
`#        enabled: "true"`
`#  jpa:`
`#    hibernate:`
`#      ddl-auto: "validate"`
`#    database-platform: "org.hibernate.dialect.HSQLDialect"`
`#  datasource:`
`#    driverClassName: "${SPRING_DRIVER_CLASS_NAME:org.hsqldb.jdbc.JDBCDriver}"`
`#    url: "${SPRING_DATASOURCE_URL:jdbc:hsqldb:file:${SQL_DATA_FOLDER:/tmp}/thingsboardDb;sql.enforce_size=false}"`
`#    username: "${SPRING_DATASOURCE_USERNAME:sa}"`
`#    password: "${SPRING_DATASOURCE_PASSWORD:}"`

* Uncomment ‘# PostgreSQL DAO Configuration’ block. Be sure to update the postgres databases username and password in the bottom two lines of the block (here, as shown, they are both “postgres”).

`# PostgreSQL DAO Configuration`
`spring:`
`  data:`
`    jpa:`
`      repositories:`
`        enabled: "true"`
`  jpa:`
`    hibernate:`
`      ddl-auto: "validate"`
`    database-platform: "org.hibernate.dialect.PostgreSQLDialect"`
`  datasource:`
`    driverClassName: "${SPRING_DRIVER_CLASS_NAME:org.postgresql.Driver}"`
`    url: "${SPRING_DATASOURCE_URL:jdbc:postgresql://localhost:5432/thingsboard}"`
`    username: "${SPRING_DATASOURCE_USERNAME:postgres}"`
`    password: "${SPRING_DATASOURCE_PASSWORD:postgres}"`

3. Run Installation Script

`# --loadDemo option will load demo data: users, devices, assets, rules, widgets.`
`sudo /usr/share/thingsboard/bin/install/install.sh --loadDemo`

![thingsboard_script](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_backend_raspi3/images/thingsboard_launch.png)

4. Start Thingsboard Service

`sudo service thingsboard start`

5. Open in your laptop broser Thingsboard URL: http://[RASPBERRY_IP]:8080/

Where [RASPBERRY_IP] is your raspberry IP address. (check it using `ifconfig`)

NOTE: It may take some minutes to be accessible. Be patient.

![thingsboard_webui](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_backend_raspi3/images/thingsboard_webui.png)


## Default users available

ThingsBoard installation contains single tenant account that is used in sample applications and contains a lot of pre-provisioned entities for demonstration purposes.

1. System Administrator: Default system administrator account.
login - sysadmin@thingsboard.org.
password - sysadmin.

2. Demo Tenant: Default tenant administrator account.
login - tenant@thingsboard.org.
password - tenant.

3. Demo tenant customers: All users have “customer” password.
* Customer A users - customer@thingsboard.org or customerA@thingsboard.org.
* Customer B users - customerB@thingsboard.org.
* Customer C users - customerC@thingsboard.org.

## First Acess - Initial config
Acess using "tenant" account, you will reach this dashboard:

![Tenant default dashboard](https://github.com/Kike-Ramirez/workshop-iot-creativecodingmadrid/blob/master/IOT_backend_raspi3/images/thingsboard_tenant_dashboard.png)

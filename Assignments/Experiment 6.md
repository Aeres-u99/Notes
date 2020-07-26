# Experiment 6

## Aim:

To containerize Apache in docker 

a) using commandline 

b) Using DOCKERFILE



### Containerization using Command line

```bash
sudo docker run --name WebServerProper -p 81:80 -t -i ubuntu /bin/bash
```

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_22.06.png)

Once inside the prompt, 

```bash
apt update && apt install apache2 
```

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_21.54.png)

```bash
service apache2 start
```

That will start the apache webserver on docker container

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_22.14.png)

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_22.16.png)

### Containerization using DOCKERFILE

Start with creating a base directory and creating two files 

```bash
mkdir DockerHTTPD && cd DockerHTTPD
```

```bash
# Write in a file named apache-conf
    Mutex file:${APACHE_LOCK_DIR} default
    PidFile ${APACHE_PID_FILE}
    Timeout 300
    KeepAlive On
    MaxKeepAliveRequests 100
    KeepAliveTimeout 5
    User ${APACHE_RUN_USER}
    Group ${APACHE_RUN_GROUP}
    HostnameLookups Off
    ErrorLog ${APACHE_LOG_DIR}/error.log
    LogLevel warn
    IncludeOptional mods-enabled/*.load
    IncludeOptional mods-enabled/*.conf
    Include ports.conf
     
    <Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
    </Directory>
    <Directory /usr/share>
        AllowOverride None
        Require all granted
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
     
    AccessFileName .htaccess
     
    <FilesMatch "^\.ht">
        Require all denied
    </FilesMatch>
     
    LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
    LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
    LogFormat "%h %l %u %t \"%r\" %>s %O" common
    LogFormat "%{Referer}i -> %U" referer
    LogFormat "%{User-agent}i" agent
     
    IncludeOptional conf-enabled/*.conf
    IncludeOptional sites-enabled/*
```

```dockerfile
    FROM ubuntu:16.04
     
    # Apache ENVs
    ENV APACHE_RUN_USER www-data
    ENV APACHE_RUN_GROUP www-data
    ENV APACHE_LOCK_DIR /var/lock/apache2
    ENV APACHE_LOG_DIR /var/log/apache2
    ENV APACHE_PID_FILE /var/run/apache2/apache2.pid
    ENV APACHE_SERVER_NAME localhost
     
    # Install services, packages and do cleanup
    RUN apt-get update \
     && apt-get install -y \
        apache2 \
     && rm -rf /var/lib/apt/lists/*
     
    # Copy files
    COPY apache-conf /etc/apache2/apache2.conf
     
    # Expose Apache
    EXPOSE 80
     
    # Launch Apache
    CMD ["/usr/sbin/apache2ctl", "-DFOREGROUND"]
```

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_22.22.png)

Build the container using 

```bash
docker build -t webserver_img .
```

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_22.31.png)

After that, simply run the resultant container and yay!

```bash
docker run -i -t -d -p 5000:80 --name=webserver_con webserver_img
```

![](../img//home/akuma/Screenshots/Cheese_Thu-16Apr20_22.34.png)



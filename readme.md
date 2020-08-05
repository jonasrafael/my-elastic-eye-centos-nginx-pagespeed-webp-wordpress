In all my life i try to find the better way to configure one server to show BSF Wordpress = Bigger, stronger and faster and maybe i gone with Pagespeed, FastCGI, PHP-FPM, FastCGI cache, SSL, security settings, .webp support. Mix and match the .conf files for your preferred configuration and traffic needs.

Testing and compatibility This has been thoroughly tested with the Nginx 1.19 stable branch and PHP 7.4 in Centos 7 and is up and running on several production sites.

# Requisites
- Vm Instance
- Centos 7
- Time!!!


# How to Start

yum update

yum upgrade

yum autoremove

yum clean all

yum install nano wget mlocate

# Acecept your SSH
#Find the PasswordAuthentication

/etc/ssh/sshd_config
sudo service sshd restart

cd /tmp

#Install the Epel repository. yum install epel-release
#Install the Remi repository.
wget http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

sudo rpm -Uvh remi-release-7*.rpm


#https://www.virtualmin.com/download.html
wget http://software.virtualmin.com/gpl/scripts/install.sh

sh ./install.sh -n srv.jonasrafael.com -m -b LEMP

/etc/yum.repos.d/nginx.repo 


[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/centos/7/$basearch/
gpgcheck=0
enabled=1
For example, if you wanted to use the repository to install MariaDB 10.3 on CentOS 7, then you could use the following yum repository configuration in /etc/yum.repos.d/MariaDB.repo:

[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.3/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
/etc/yum.repos.d/MariaDB.repo
sudo yum install gcc-c++ pcre-devel zlib-devel make unzip libuuid-devel
yum install redhat-rpm-config make openssl-devel libxml2-devel libxslt-devel gd-devel perl-ExtUtils-Embed GeoIP-devel gperftools-devel

bash <(curl -f -L -sS https://ngxpagespeed.com/install) \
     --nginx-version latest

[root@srv tmp]# bash <(curl -f -L -sS https://ngxpagespeed.com/install) -n 1.13.2 -v 1.13.35.2-stable -m

#Still Install

yum install redhat-rpm-config make openssl-devel libxml2-devel libxslt-devel gd-devel perl-ExtUtils-Embed GeoIP-devel gperftools-devel

#And Now, the PageSpeed Mod
#https://www.modpagespeed.com/doc/build_ngx_pagespeed_from_source
bash <(curl -f -L -sS https://ngxpagespeed.com/install)  -n 1.19.1 -v 1.13.35.2 -m


#Good To Read
- https://www.liquidweb.com/kb/update-mariadb-from-10-0-to-10-3-on-centos-7/
- https://www.prado.lt/5-minute-upgrade-nginx-1-12-to-1-17-on-centos-7-rhel-7
- https://www.mynotepaper.com/install-latest-php-php-fpm-on-centos-7/

#Ex My Configuration Files
configure arguments: --prefix=/etc/nginx --sbin-path=/usr/sbin/nginx --modules-path=/usr/lib64/nginx/modules --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --pid-path=/var/run/nginx.pid --lock-path=/var/run/nginx.lock --http-client-body-temp-path=/var/cache/nginx/client_temp --http-proxy-temp-path=/var/cache/nginx/proxy_temp --http-fastcgi-temp-path=/var/cache/nginx/fastcgi_temp --http-uwsgi-temp-path=/var/cache/nginx/uwsgi_temp --http-scgi-temp-path=/var/cache/nginx/scgi_temp --user=nginx --group=nginx --with-compat --with-file-aio --with-threads --with-http_addition_module --with-http_auth_request_module --with-http_dav_module --with-http_flv_module --with-http_gunzip_module --with-http_gzip_static_module --with-http_mp4_module --with-http_random_index_module --with-http_realip_module --with-http_secure_link_module --with-http_slice_module --with-http_ssl_module --with-http_stub_status_module --with-http_sub_module --with-http_v2_module --with-mail --with-mail_ssl_module --with-stream --with-stream_realip_module --with-stream_ssl_module --with-stream_ssl_preread_module --with-cc-opt='-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector-strong --param=ssp-buffer-size=4 -grecord-gcc-switches -m64 -mtune=generic -fPIC' --with-ld-opt='-Wl,-z,relro -Wl,-z,now -pie'



# Config your database to receive biggest files;
db mysql -u root -p yourdatabase <

--> Update the my.cnf
max_allowed_packet=64M

# Uptate to php 7.4
https://srv.jonasrafael.com:10000/package-updates/?xnavigation=1
# Enable just the REMI 74.

wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
wget https://rpms.remirepo.net/enterprise/remi-release-7.rpm
rpm -Uvh remi-release-7.rpm epel-release-latest-7.noarch.rpm


sudo apt install php7.4-curl php7.4-mbstring php7.4-bz2 php7.4-readline php7.4-intl

sudo apt install php7.4-bcmath php7.4-bz2 php7.4-curl php7.4-intl php7.4-mbstring php7.4-mysql php7.4-readline php7.4-xml php7.4-zip`


# Remove Old Versions of PHP
yum list installed | grep php
yum remove -y php72*

yum install php-bcmath

yum install php-imagick
yum install php-soap


# Wp-Rocket NGinx
- https://github.com/SatelliteWP/rocket-nginx
sudo nano /etc/nginx/nginx.conf
    client_max_body_size 100M;

* sudo yum install libwebp-tools
Yum install optipng & jpegoptim

# Web P
https://wpspeedmatters.com/serve-webp-in-wordpress/
https://wordpress.org/plugins/webp-express/#%0Ai%20am%20on%20nginx%20or%20openresty%0A

yum install php-pecl-zip


## How to use
* Pick a /conf.d file and mix to taste. Check for #TODO for `example.com` fields that need editing.
* Drop nginx.conf and the rest of these folders into /etc/nginx on your Linux server.
* `sudo nginx -t` to check for typos
* `sudo systemctl reload nginx`
* You're live.

# Prevent Attacks
 
sudo yum install fail2ban

iptables -A INPUT –p tcp –m state --state NEW –j DROP
iptables -A INPUT -p tcp -m state --state NEW -m limit --limit 2/second --limit-burst 2 -j ACCEPT
iptables -A INPUT -p icmp -m limit --limit 2/second --limit-burst 2 -j ACCEPT
iptables -A INPUT -p tcp --tcp-flags ALL FIN,PSH,URG -j DROP


# Read Also

- https://iserversupport.com/how-to-install-nginx-php-fpm-mysql-with-pagespeed-and-memcached-for-high-performance/?__cf_chl_jschl_tk__=d7c28cfbdbcf62c70b33d1876ba2b3407378c89b-1596567116-0-ATEiaiVFy4HVJBCVg4UHPK2B7nI-dQ2sYedRMEdn3rBwngNc5JVxdLOUAB_WgNRlb0vhruPIyxDBwFQeEjkA_GDW64HZUfeVIsnEIEfNatVvgzfSsu8n62GGK2CJrtCazDNh37BH55hMR4JBr6HTnn7x9kHlkLw9dhVa5DtTsM-aL7Dm5F0kXACxOaYRI8OAAuprnyjjTZMwRuH0eu5abADq90rkjTXoEIq_U4IoqJZrYeEcAQC1qYddPrk4c5Wg_F9T-wOha2pS-PEkM3hdC6zDzCjWfDS5idRQB6kk2yhjhX2Kuznzwv6lX6lz12-GBr-UdOY1X-m52kWYsND3Y9yieGXzC8jgXva6_oIRylIqa60JHqrJ2U-i_QPx3CwZQ8a4hVKPFgwoy9HM8BGn-Jg



# Wordfence Adjusts on Iptables
sudo iptables -t filter -A INPUT -p tcp --dport 443 -j ACCEPT
sudo iptables -t filter -A OUTPUT -p tcp --dport 443 -j ACCEPT

## In progress

# Advanced - Log Rotation:
https://linoxide.com/linux-how-to/install-logrotate-configure-nginx-log-rotation/
https://www.obstance.com/web/using-logrotate-to-rotate-php5-fpm-logs


# Clear Cache
touch /var/ngx_pagespeed_cache/cache.flush
nginx -V 2>&1 | grep nginx-cache-purge -o

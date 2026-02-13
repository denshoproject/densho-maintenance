# densho-maintenance

This repo provides static HTML outage pages for Densho web properties. It is designed for use on a Debian host with nginx installed, and DNS for the affected site repointed at the host's public nginx IP. 

Each directory contains an `index.html` file for the associated property that can be edited with information about the particular outage. 

## Installation

``` bash
ssh ansible@PROXY

# Install dependencies
apt install git nginx

# Get densho-maintenance
git-clone http://github.com/denshoproject/densho-maintenance.git
mv densho-maintenance /opt/

# Install nginx conf
cd /etc/nginx/sites-enabled/
ln -s /opt/densho-maintenance/conf/ddrpublic.conf
ln -s /opt/densho-maintenance/conf/encycfront.conf
ln -s /opt/densho-maintenance/conf/encycrg.conf
ln -s /opt/densho-maintenance/conf/maps.conf
ln -s /opt/densho-maintenance/conf/nikkeijin.conf
ln -s /opt/densho-maintenance/conf/www.conf

# Install SSL certs to
# - /etc/nginx/ssl/proxy_ssl_certificate
# - /etc/nginx/ssl/proxy_ssl_certificate_key
chown root.root /etc/nginx/ssl/proxy_ssl_certificate*
chmod 0600 /etc/nginx/ssl/proxy_ssl_certificate*

# Restart nginx
service nginx reload
```


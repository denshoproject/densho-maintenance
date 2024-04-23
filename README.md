# densho-maintenance


## Installation

``` bash
ssh ansible@PROXY

# Install dependencies
apt install git nginx-light

# Get densho-maintenance
git-clone http://github.com/denshoproject/densho-maintenance.git
mv densho-maintenance /opt/

# Install nginx conf
cd /etc/nginx/sites-enabled/
ln -s /opt/densho-maintenance/conf/ddrpublic.conf
ln -s /opt/densho-maintenance/conf/encycfront.conf
ln -s /opt/densho-maintenance/conf/encycrg.conf

# Install SSL certs to
# - /etc/nginx/ssl/proxy_ssl_certificate
# - /etc/nginx/ssl/proxy_ssl_certificate_key
chown root.root /etc/nginx/ssl/proxy_ssl_certificate*
chmod 0600 /etc/nginx/ssl/proxy_ssl_certificate*

# Restart nginx
service nginx reload
```

# Stop container connected on port 80: docker container stop <container_id>
# Build image: 
docker build -t certbot -f Dockerfile.prod .

# Launch container to identify new domains: 
docker run -v /etc/letsencrypt:/etc/letsencrypt -p 80:80 -p 443:443 -it certbot certonly --standalone -d planitools.com -d www.planitools.com -d planitrack.planitools.com

# There is a declinaison to have different subfolders in etc/letsencrypt for different certificates for each subdomains
# If you do so then you will need to adjust the SSL directives in the nginx conf
-docker run -v /etc/letsencrypt:/etc/letsencrypt -p 80:80 -p 443:443 -it certbot certonly --standalone -d -cert-name planitools.com -d -cert-name www.planitools.com -d -cert-name planitrack.planitools.com -cert-name

# Launch container to renew certificates: 
docker run -v /etc/letsencrypt:/etc/letsencrypt -p 80:80 -p 443:443 -it certbot renew

# Restart the proxy container on port 80: 
docker container start <container_id>
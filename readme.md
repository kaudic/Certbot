# Stop container connected on port 80: docker container stop <container_id>
# Build image: docker build -t certbot -f Dockerfile.prod .
# Launch container: docker run -v /etc/letsencrypt:/etc/letsencrypt -p 80:80 -p 443:443 -it certbot certonly --standalone -d www.planitools.com -d planitrack.planitools.com
# Restart the proxy container on port 80: docker container start <container_id>
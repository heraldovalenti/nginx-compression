# Getting started
As a pre-requisite you will need [Docker](https://docs.docker.com/get-docker/) and [docker-compose](https://docs.docker.com/compose/install/).  

Then, you only need to run `docker-compose up -d` and the server will start, and you can browse the HTML contents in `html` folder with your browser in `https://localhost/`.  

Note that this requires you to accept the untrusted certificate, you can either trust the default certificate, or generate your own one (see next section).

# Change domain name
1. Update the `CN` field on `req.conf` with your desired domain name.
2. Re-generate the TLS certificate with `openssl req -x509 -nodes -days 730 -newkey rsa:2048 -keyout domain.key -out domain.crt -config req.conf -extensions 'v3_req'`.
3. Modify your /etc/hosts files to point your new domain to 127.0.0.1, e.g.:
```
127.0.0.1    example.io
```
4. Restart the server with `docker-compose restart`.
5. Use your browser to access the web server with your new domain name, e.g.: https://example.io/.

# Compression configuration
This server is configured to gzip content `text/plain` and `application/javascript`, but you can add more mime types in the `nginx.conf` file and restart the server to reflect your changes.  
Visit for more details [NGINX Docs - Compression](https://docs.nginx.com/nginx/admin-guide/web-server/compression/).

# HTML files
You can update the HTML contents in the `html` folder and then hit refresh in your browser.  
The example content is taken from [NGINX Docs - Compression](https://docs.nginx.com/nginx/admin-guide/web-server/compression/).

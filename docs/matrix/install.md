# Installing a Matrix Server

This is a tutorial for setting up a Matrix server on an Ubuntu machine.

## 0. Grab a Domain and a Server

You will need to have access to a server with Ubuntu (a VPS or a dedicated server works well) and a domain name. You can get a decent VPS from DigitalOcean or OVH in many locations around the world, and a low cost domain from PorkBun.

## 1. Update Your Packages

It's never a bad idea to update your package lists, then upgrade all of the software you have on your server before starting.

```
sudo apt update
sudo apt upgrade
```

## 2. Install the Matrix Server (Synapse)

Matrix's backend, known as Synapse, can be installed from the Ubuntu package archive.

```
sudo apt install matrix-synapse
```

Refresh the newly installed service.

```
sudo service matrix-synapse restart
```

To test if Matrix was installed, you can send a GET request to port 8008. If the server is running, you should see a static HTML page.

```
wget -qO- localhost:8008
```

## 3. Nginx Reverse Proxy (plus SSL)

To add encryption to your server, you'll need to use a reverse proxy. In this tutorial, Nginx will be used, but Caddy and Apache are also good options. Begin by installing Nginx...

```
sudo apt install nginx
```

...and make sure it is running by visiting your server's public IP address in your browser of choice. You should see a screen with the text "Welcome to nginx!"

Next, you should add a configuration file for Matrix. Enter the conf.d folder, and add the folowing configuration to `matrix.conf`. I've adapted this configuration from [atlantic.net](https://www.atlantic.net/dedicated-server-hosting/how-to-install-matrix-synapse-with-nginx-and-lets-encrypt-ssl-on-debian-10/)

```
server {
    listen 80;
    server_name YOURMATRIXDOMAINNAME;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name YOURMATRIXDOMAINNAME;

    ssl_certificate /etc/letsencrypt/live/YOURMATRIXDOMAINNAME/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/YOURMATRIXDOMAINNAME/privkey.pem;

    location / {
        proxy_pass http://localhost:8008;
        proxy_set_header X-Forwarded-For $remote_addr;
       # Nginx by default only allows file uploads up to 1M in size
        # Increase client_max_body_size to match max_upload_size defined in homeserver.yaml
        client_max_body_size 10M;
    }

    location /.well-known/matrix/ {
        root /var/www/static;
    }
}
```

Make sure to replace `YOURMATRIXDOMAINNAME` with the domain of your choice. You'll also have to edit the DNS records for your domain to point to the IP address of your server.

**Before your restart nginx**, a few more tasks need to be done. First, enter `/var/www/`, and create a folder called `static`. Next, create a folder called `.well-known`, enter that folder, then create a folder called `matrix`. Finally, create and edit a file called `server`. This file will tell other Matrix servers how to communicate with you. Add the following text to that file.

```
{ "m.server": "YOURMATRIXDOMAINNAME:443" }
```

(Replacing `YOURMATRIXDOMAINNAME` with your domain of choice, of course)

Now, let's install certbot. Install Certbot and an SSL certficate with the following commands:

```
sudo apt-get install python3-certbot-nginx
sudo certbot certonly --nginx -d YOURMATRIXDOMAINNAME
```

Now it's time to restart nginx.

```
sudo service nginx restart
```

Congrats, you've just installed Matrix! Test your configuration with [Element](app.element.io) (set "homeserver" to your domain).

## 4. Extensions

The default SQLite database that comes with Matrix works well for small instances and testing, but you'll want to upgrade to Postgresql for bigger instances. Take a look at [this tutorial for more information on that](https://matrix-org.github.io/synapse/latest/postgres.html).
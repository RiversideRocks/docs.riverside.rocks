# Varnish Quickstart

After installing Varnish, make sure that it is running:

```
sudo service varnish status
```

An example of an operating Varnish server will look like this:

![](https://i.imgur.com/tTGkHut.png)

*If you have an error, run `sudo service varnish start` to start it*

By default, Varnish's HTTP server will run on port 6081. This will be useful later when configuring a reverse proxy in front of Varnish.

Enter Varnish's directory and view the configuration files. This directory is `/etc/varnish`. Open the default.vcl file with your favorite editor (you'll need root to edit files in this directory). You should see something like this:

![](https://i.imgur.com/aT6QpYb.png)

Varnish breaks this default file up into three sections: vcl_recv, vcl_backend_response, and vcl_deliver. vcl_recv is used to manipulate a request before it is looked up in the cache, vcl_backend_response is used to manipulate a request after it is looked up in the cache, and vcl_deliver is used to make changes before the request is sent.
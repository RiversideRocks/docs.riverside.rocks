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

Paste the following line under `vcl_backend_response`.

```
set beresp.ttl = 1d;
```
This tells Varnish to cache all content for one day, then purge it from the cache. Reload Varnish (`sudo service varnish restart`) to save and apply the changes.

Yay! You just set up Varnish. Set your backend program to listen to port 8080, then visit [localhost:6081](http://localhost:6081). You should see your backend program running. To see if Varnish is working, open your browser's developer tools, and reload the page. Take a look at the [age](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Age) header. If it shows a value that is more than 0, your content has been cached into memory.
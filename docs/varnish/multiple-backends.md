# Multiple Backends

A common task is to configure more than one backend that Varish will pull from. If you've just installed Varnish, you should have one default backend, that looks something like this:

```
backend default {
    .host = "127.0.0.1";
    .port = "3000";
}
```

Adding another backend is simple, all you'll need to create is a new name and port. For example, if I had a service running on port 4000, I would add the following:

```
backend newservice {
    .host = "127.0.0.1";
    .port = "4000";
}
```
<blockquote>
Note that you need to use all backends that you define. Varnish will crash and throw an error if you don't.
</blockquote>

Next, tell Varnish when you want to use the backend under the `vcl_recv` section. For example, if you had a website running on `app.example.com`, you could tell varnish to set the backend to `newservice` like so:

```
if (req.http.host ~ "app.example.com")
{
    set req.backend_hint = newservice;
}
```

<blockquote>
By default, Varnish will fall back to the `default` backend. 
</blockquote>

Another common task is setting the backend when a certain URL pattern is matched. If you want to set the `newservice` backend when an image file is requested, you could set that backend like so:

```
if (req.url ~ "^[^?]*\.(png|jpg|gif|jpeg)(\?.*)?$")
{
    set req.backend_hint = newservice;
}
```
# Introduction to Varnish and Caching

Sometimes, it's impossible to streamline your code even more. Some processes are always going to be costly in terms of CPU and memory. Thankfully, a solution to this is using a caching program. Instead of generating a dynamic page multiple times, a cache program will the generated page in memory and serve the page from memory to users.

![](https://i.imgur.com/Rp9hlHm.jpg)

## Benefits of Cache

### Saves CPU/System Load

A caching program reduce load on the CPU by stopping the unneeded generation of dynamic pages multiple times. This is especially true for dynamic pages pulling from databases like MySQL and PostgreSQL. Instead of regenerating a page that pulls from a database every time a user requests it, caching programs will retrieve said page only a fraction of the time.

### Speeds up Content Delivery

Varnish Cache's website claims to speed up websites by "a factor of 300 - 1000x, depending on your architecture". This is true because reading memory is much faster than generating a page or reading content from the disk.

## Downsides of Cache

### Uses Memory

Everything Varnish caches is saved in memory, which has upsides (see "Speeds up Content Delivery") and downsides. On systems with limited memory, Varnish will run out of memory quickly if caching a great deal of image and video files. To avoid this issue, consider giving Varnish more RAM or configuring your VCL file to bypass video and image files.

### Unintended Side Effects <!-- tom scott steam video -->

If Varnish or any caching program is configured incorrectly, there can be unintended consiquences, such as the caching of cookies or pages with user infomation. **NEVER CACHE PAGES WITH COOKIES!** Cookies can often contain information unique to a logged in user, and if cached, they will be made public to anyone who accesses the website or said page. Hackers (or, really anyone with technical knowledge) can use cookies to log steal account information. If you still aren't convinced, check out [Tom Scott's video on the time Steam made this mistake](https://youtu.be/dkSslseq9Y8).

## Cloud Varnish

If you're interested in running Varnish Cache in the cloud, I suggest you check out a cloud reverse proxy like [Fastly](https://www.fastly.com) which is based off Varnish.
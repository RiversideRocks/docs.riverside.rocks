# Cloudflare's Features

This is a list of features that Cloudflare offers.

## Good Features

### Caching

* Default caching of many static assets (CSS, JS, Images, etc.)
* Optional caching of any other filetype

### DDoS Protection

* 155tbps network
* Uses AI to block bots/DDOS attacks
* L3/L4 + L7 protection
* Hundreds of edge locations to absorb attacks

### Email Forwarding
* Options to forward incoming emails to a domain to any 3rd party email provider

### DNS
* Fast DNS propogation times
* Unlimited DNS traffic for you domain on any plan

### DNS Resolver
* 1.1.1.1 is free for all users, no signup needed

## Drawbacks/Bad Features

* Videos cannot be cached on the free plan
* DDoS Protection/Bot filter can block legitimate users and [command line tools like wget](https://superuser.com/questions/888507/problems-with-wget-to-a-cloudflare-hosted-site-503-service-unavailable)
* [Harsh](https://i.imgur.com/qKl1Qqc.png) on Tor/VPN users
* Possible privacy concerns: a company that controls 20% of sites on the internet can gain a large amount of information on any given user. [Hackers have exploited issues in the Cloudflare network in the past, raising possible security concerns.](https://en.wikipedia.org/wiki/Cloudbleed)

## Cloudflare Policies

If you want to view how Cloudflare thinks of itself as a service provider, read up on these links. I won't be commenting on Cloudflare's moderation practices on this site.

* [https://blog.cloudflare.com/cloudflares-abuse-policies-and-approach/](https://blog.cloudflare.com/cloudflares-abuse-policies-and-approach/)
* [https://blog.cloudflare.com/kiwifarms-blocked/](https://blog.cloudflare.com/kiwifarms-blocked/)
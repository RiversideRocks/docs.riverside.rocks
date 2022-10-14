# Proxies in the Cloud

There are many options for reverse proxy services in the Cloud. This document provides basic facts on a variety of services.

## Cloudflare

* Lowest Tier: Free
* Tier System: Monthly/Base Fee + Free Bandwidth
* Bandwidth Price: $0/GB
* Number of Datacenters/PoPs: 275, see [cloudflare.com](https://www.cloudflare.com/network/)
* Network Capactiy: 155tbps

## Fastly

* Lowest Tier: Contact sales (base price: $50 a month plus bandwidth charges)
* Tier System: Base Fee ($50) + Bandwidth paid for by GB
* Bandwidth Price: $0.12 exgress traffic (North America), see [fastly.com/pricing](https://www.fastly.com/pricing)
* Number of Datacenters/PoPs: 81 unique, some locations have multiple PoPs, see [fastly.com/network-map/](https://www.fastly.com/network-map/)
* Network Capacity: 215tbps

## Akamai

* Lowest Tier: (contact for price)
* Tier System: Base fee (?) + Bandwidth paid for by GB
* Bandwidth Price: $0.35 North America (unoffical source: https://www.keycdn.com/akamai-pricing)
* Number of Datacenters/PoPs: Almost every country (minus China, Syria, North Korea, Sierra Leone, and a few others), see https://www.akamai.com/site/en/documents/akamai/points-of-presence-countries.pdf *
* Network Capactity: Unknown, but they have boasted spikes of 250tbps, meaning their network can likley handle much more than 250tbps **

`*` It's safe to assume some locations on this map are not real, the chances of Akamai having servers in Antartica and Christmas Island are slim
`**` [Akamai's Global Page](https://gnet.akamai.com/) claims they are currently transfering 147tbps, however, they admit this data is not real

## KeyCDN

* Lowest Tier: $4/month minimum charge
* Tier System: Base fee ($4/month) + Bandwidth paid for by GB
* Bandwidth Price: $0.04 (North America)
* Number of Datacenters/PoPs: 40+ PoPs, 30+ countries, see [keycdn.com/network](https://www.keycdn.com/network)
* Network Capacity: ?

## Cachefly

* Lowest Tier: "Essential", includes 10TB of traffic (contact for price)
* Tier System: Base fee (contact to view) + Fixed ammount of data included, unless on "performance" plan where transfer is unmetered
* Bandwidth Price: Not metered by the GB, but included in a plan
* Number of Datacenters/PoPs: 60+ Locations
* Network Capacity: 1-5tbps (PeeringDB)

## Cloudfront

* Lowest Tier:

# To sum it up


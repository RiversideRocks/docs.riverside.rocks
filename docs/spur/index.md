# Spur

Spur is an IP data collection service. They harvest data on IP address, such as user count, VPN/proxy status, and VPN/proxy usage.

## Interesting Features

Spur provides unique statistics for IP addresses, such as device count and "behaviors", such as Tor usage. They likley source this data from companies that sell [internet backbone data](https://www.vice.com/en/article/jg84yy/data-brokers-netflow-data-team-cymru), although that has never been confirmed. (See also: [Team Cymru's responses to this article and others like it](https://www.team-cymru.com/post/team-cymru-myth-vs-fact))

## Accuracy

Spur's accuracy varies from excellent to poor. Their VPN detection is excellent and is almost always correct, their device behaviors and often accurate, and their device count is rarley accurate. For example, Spur says my home wifi's IP address has one mobile device, but the reality is that there are at least 4-5 phones, 4 laptops, and 5 IoT devices connected to the network. Most data is brilliant, but take device counts with a grain of salt.
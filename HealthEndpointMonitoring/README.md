# Health Endpoint Monitoring Pattern

Applications that contains many sub systems require advanced monitoring of the health of this application and its subsystems, this design pattern allow you to have an elegent way to achieve that.

Suppose you have a web site that uses a sql database a search server a cache store and a content delivery network, assuming that the application, if you just include regular monitoring front of the web site you will always recive status `200` which will indeicate the web is is fine, however behind the seen maybe the cache is failing and all items store are no longer reverted internally or maybe the images css and files are all retrived directly from the server and not served by the CDN, in that case the regular monitoring does not tell much about the sub systems *Health Endpoint Monitoring Pattern* will help you detect some of this internal issue

This pettern contains two parts:

- An Endpoint exposed by the web site in this example that check all the sub systems and return status:
    - Status of the web site and it may run functional tests
    - Database status
    - Search status
    - Cache status
    - CDN
- A monitoring tool that check:
    - Website by utilising this Endpoint
    - SSL and check if the site is secured
    - Performance to check latency
    - Geo Pinging


That way you can gather a lot of data and have a realistic view of the application health, when designing this pattern think of what information needs to be exposed by the end point and how it must be presented, attackers may use this information so must be secured, think of what the monitoring tool will be analysing for example latency from diffrent geo-locations


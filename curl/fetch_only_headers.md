# Fetch Only URL Info

Use the -I flag to display headers, protocol and other info for url w/o body

```bash
$ curl -I https://reddit.com

HTTP/2 301
retry-after: 0
location: https://www.reddit.com/
accept-ranges: bytes
date: Wed, 15 Jul 2020 14:15:26 GMT
via: 1.1 varnish
x-served-by: cache-fra19183-FRA
x-cache: HIT
x-cache-hits: 0
x-timer: S1594822526.468800,VS0,VE0
cache-control: private, max-age=3600
strict-transport-security: max-age=15552000; includeSubDomains; preload
server: snooserv
content-length: 0
```

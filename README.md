# docker-dnsmasq

Entrypoint is ```dnsmasq -k``` which puts dnsmasq to the foreground. Default configuration is in ```/etc/dnsmasq.conf``` and can be overridden. Configuration can also be passed in as ```command```.

## Example in compose

I can't remember why i'm not just mounting over /etc/hosts, but here's an example using custom hosts file:

```yaml
version: '3'
  services:
  dnsmasq:
    container_name: dnsmasq
    image: ghcr.io/chrisanderton/docker-dnsmasq:v2.8.9
    command:
      - --no-hosts
      - --addn-hosts=/etc/hosts.custom
      - -q
      - --log-facility=-
    volumes:
      - ./hosts.custom:/etc/hosts.custom:ro
```

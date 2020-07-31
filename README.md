# Local_Grafana

A quick docker-compose configuration to spin up a grafana instance with loki, promtail, influxdb, and chronograf.
In addition, it spins up a (pretty basic) rust-based service that tracks SSH attempts, queries a geoIP database with their origin IPs, and spits them into influxdb.

# Usage

- Get GeoLite2-City.mmdb from MaxMind (https://dev.maxmind.com/geoip/geoip2/geolite2/).
- Place GeoLite2-City.mmdb in ./data/authmap/.
- `docker-compose up -d`

# Notes
- Don't publicly expose your influxdb instance. This repo includes an influxdb configuration with auth disabled (default) and flux enabled.
- All containers are on the same network, named `loki`
- Both influxQL and Flux are enabled. Grafana has beta-level support for Flux.
- Authmap, the service that fetches coordinates from SSH query origin IPs, is pretty basic and may not be robust or performant.

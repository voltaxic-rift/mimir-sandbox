# Mimir read-write mode test

WIP

```
docker-compose up -d
```

```
# k6 test
go install go.k6.io/xk6/cmd/xk6@latest
~/go/bin/xk6 build --with github.com/grafana/xk6-client-prometheus-remote@latest
./k6 run ~/dev/src/github.com/grafana/mimir/operations/k6/load-testing-with-k6.js \
    -e K6_WRITE_HOSTNAME="localhost:9011" \
    -e K6_READ_HOSTNAME="localhost:9010" \
    -e K6_WRITE_REQUEST_RATE="10000" \
    -e K6_WRITE_SERIES_PER_REQUEST="15" \
    -e K6_DURATION_MIN="30" \
    -e K6_READ_REQUEST_RATE="10" \
    -e K6_SCRAPE_INTERVAL_SECONDS="60" \
    -e K6_RAMP_UP_MIN="2" \
    -e K6_TENANT_ID="demo"
```

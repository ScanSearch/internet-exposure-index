# Internet Exposure Index

What is actually reachable on the public internet right now — exposed databases, remote-access ports and obsolete TLS — counted over a **rolling 30-day window** and refreshed weekly.

**Updated:** 2026-08-10 · **Window:** last 30 days · **Most recent scan:** 2026-08-10

Exposure numbers age badly. A host that answered on port 27017 last year may be patched, firewalled or gone, so a cumulative all-time count quietly inflates every figure it reports. Everything here is restricted to services observed in the last 30 days, and the window moves with each refresh.

## Exposed datastores

Databases answering on the public internet:

| Datastore | Hosts seen (30d) |
|---|---:|
| mongodb | 300,696 |
| redis | 185,254 |
| mysql | 77,253 |
| influxdb | 9,947 |
| couchdb | 2,184 |
| clickhouse | 422 |
| cassandra | 419 |
| postgresql | 246 |
| elasticsearch | 139 |
| memcached | 74 |

## Remote-access surface

The services that show up first in ransomware post-mortems:

| Service | Hosts seen (30d) |
|---|---:|
| ssh | 2,500,217 |
| ftp | 253,854 |
| rdp | 196,910 |
| telnet | 182,413 |
| proxmox | 114,863 |
| vnc | 93,269 |
| smb | 5,867 |

## TLS versions

Obsolete TLS (1.0/1.1/SSLv3) still answers on **6,131** hosts in this window:

| Version | Hosts (30d) | Share |
|---|---:|---:|
| TLS 1.3 | 7,949,871 | 76.25% |
| TLS 1.2 | 2,469,889 | 23.69% |
| TLS 1.0 | 6,030 | 0.06% |
| TLS 1.1 | 101 | 0.0% |

## Files

| File | Contents |
|---|---|
| [`latest.json`](latest.json) | headline counts, structured |
| [`exposed-services.csv`](exposed-services.csv) | top 150 services by hosts seen |
| [`exposed-databases.csv`](exposed-databases.csv) | datastores reachable from the internet |
| [`remote-access.csv`](remote-access.csv) | RDP, SSH, Telnet, VNC, FTP, SMB |
| [`top-ports.csv`](top-ports.csv) | 100 most-answered ports |
| [`by-country.csv`](by-country.csv) | hosts seen per country |
| [`tls-versions.csv`](tls-versions.csv) | TLS/SSL version distribution |
| [`history.csv`](history.csv) | one row per refresh — the series starts 2026-07 and compounds |

```bash
curl -s https://raw.githubusercontent.com/ScanSearch/internet-exposure-index/main/latest.json
```

## Method and honest limits

Figures come from active scanning: a host is counted when a service answered during the last 30 days. Most-answered ports in this window: 443, 80, 8080, 22, 3000.

**This is a sample of the internet, not a census.** It covers the ranges and ports that were scanned in the window, so treat the numbers as a floor and a trend, never as a total. Counts also mix genuinely misconfigured hosts with deliberate honeypots — every internet-wide scan has that problem, including the commercial ones.

Only aggregate counts are published. No IP addresses, no banners, no hostnames — the generator refuses to write a file containing anything IP-shaped.

## Where the numbers come from

[ScanSearch](https://scansearch.net/en/products/realtime-exposure/?utm_source=github&utm_medium=repo&utm_campaign=internet-exposure-index) is an on-demand internet scanner: you launch your own scan against a range, ASN or country and get current open ports and services in minutes, rather than querying an index someone else crawled months ago. This dataset is a by-product of that pipeline.

- [Run your own scan](https://scansearch.net/en/products/realtime-exposure/?utm_source=github&utm_medium=repo&utm_campaign=internet-exposure-index)
- [scansearch-python](https://github.com/ScanSearch/scansearch-python) — official Python SDK and CLI
- [Kaggle: Global Internet Exposure Statistics](https://www.kaggle.com/datasets/buildtm/global-internet-exposure-statistics) — cumulative companion dataset

---
*Auto-generated weekly. Do not edit by hand.*

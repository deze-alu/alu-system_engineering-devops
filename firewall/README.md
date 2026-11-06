# Firewall

Install the `ufw` firewall on web-01 and block all incoming traffic
except the ports the web stack needs.

## Requirements

- Ubuntu 16.04 LTS
- Bash scripts start with `#!/usr/bin/env bash`, followed by a comment
  explaining what the script does
- All Bash scripts are executable and pass Shellcheck

## Files

| File | Description |
| ---- | ----------- |
| `0-block_all_incoming_traffic_but` | ufw commands that deny all incoming traffic except TCP ports 22 (SSH), 443 (HTTPS) and 80 (HTTP) |

## Usage

```
$ sudo ./0-block_all_incoming_traffic_but
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
443/tcp (v6)               ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
```

Port 22 is allowed before `ufw enable` runs. Once the firewall is on,
any port that isn't allowed silently drops connections, so blocking 22
would lock you out of the server.

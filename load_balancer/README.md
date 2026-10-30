# Load balancer

Bash scripts that add a second Nginx web server with a custom response
header and put both web servers behind an HAProxy load balancer.

## Servers

| Name | Role |
| ---- | ---- |
| `7268-web-01` | Nginx web server |
| `7268-web-02` | Nginx web server |
| `7268-lb-01` | HAProxy load balancer |

## Requirements

- Ubuntu 16.04 LTS
- Bash scripts start with `#!/usr/bin/env bash`, followed by a comment
  explaining what the script does
- All Bash scripts are executable and pass Shellcheck

## Files

| File | Description |
| ---- | ----------- |
| `0-custom_http_response_header` | Configure Nginx like web-01 and add an `X-Served-By` response header containing the server's hostname |
| `1-install_load_balancer` | Install HAProxy on lb-01 and distribute traffic between web-01 and web-02 using roundrobin |

## Usage

```
$ curl -sI 13.135.166.215 | grep X-Served-By
X-Served-By: 7268-web-01
$ curl -sI 18.133.221.184 | grep X-Served-By
X-Served-By: 7268-web-02

$ curl -sI 35.177.182.1 | grep X-Served-By
X-Served-By: 7268-web-01
$ curl -sI 35.177.182.1 | grep X-Served-By
X-Served-By: 7268-web-02
```

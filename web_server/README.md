# Web server

Bash scripts that transfer files to a remote Ubuntu server and install and
configure the Nginx web server on it.

## Requirements

- Ubuntu 20.04 LTS
- Bash scripts start with `#!/usr/bin/env bash`, followed by a comment
  explaining what the script does
- All Bash scripts are executable

## Files

| File | Description |
| ---- | ----------- |
| `0-transfer_file` | Transfer a file to a user's home directory on a server with `scp`, with strict host key checking disabled |
| `1-install_nginx_web_server` | Install Nginx on a new Ubuntu machine, listening on port 80 and serving a page containing `Holberton School` |
| `3-redirection` | Same as `1-install_nginx_web_server`, plus `/redirect_me` returns a `301 Moved Permanently` redirect |
| `4-not_found_page_404` | Same as `3-redirection`, plus a custom 404 page containing `Ceci n'est pas une page` |
| `5-design_a_beautiful_404_page.html` | A simple custom 404 page containing `Ceci n'est pas une page` |

## Usage

```
$ ./0-transfer_file
Usage: 0-transfer_file PATH_TO_FILE IP USERNAME PATH_TO_SSH_KEY
$ ./0-transfer_file some_page.html 8.8.8.8 ubuntu ~/.ssh/school
some_page.html                                100%   12     0.1KB/s   00:00

# on the server, as root
$ ./1-install_nginx_web_server > /dev/null 2>&1
$ curl localhost
Holberton School for the win!

$ curl -sI localhost/redirect_me/
HTTP/1.1 301 Moved Permanently
Location: https://www.youtube.com/watch?v=QH2-TGUlwu4

$ curl localhost/xyzfoo
Ceci n'est pas une page
```

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

## Usage

```
$ ./0-transfer_file
Usage: 0-transfer_file PATH_TO_FILE IP USERNAME PATH_TO_SSH_KEY
$ ./0-transfer_file some_page.html 8.8.8.8 ubuntu ~/.ssh/school
some_page.html                                100%   12     0.1KB/s   00:00
```

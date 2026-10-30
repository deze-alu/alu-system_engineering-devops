# SSH

Bash scripts and configuration files for connecting to a remote Ubuntu
server with SSH and RSA key pairs.

## Requirements

- Ubuntu 20.04 LTS
- Bash scripts start with `#!/usr/bin/env bash`, followed by a comment
  explaining what the script does
- All Bash scripts are executable

## Files

| File | Description |
| ---- | ----------- |
| `0-use_a_private_key` | Connect to the server with the private key `~/.ssh/school` as the `ubuntu` user |
| `1-create_ssh_key_pair` | Create a 4096-bit RSA key pair named `school`, protected by the passphrase `betty` |

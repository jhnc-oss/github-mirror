# GitHub Mirror

[![mirror](https://github.com/jhnc-oss/github-mirror/actions/workflows/mirror.yml/badge.svg)](https://github.com/jhnc-oss/github-mirror/actions/workflows/mirror.yml)
[![License](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)

Mirrors repositories to GitHub.

## Add Mirror

:warning: *All branches which aren't in the upstream repository are lost*.

1. Create a **fork** (if on GitHub) or an **empty destination repository**, same name as upstream is recommended
2. **Generate SSH keys**: `ssh-keygen -t ed25519 -C github-mirror`
   - Add the *private* key as a new secret to this project (`SSH_PRIVATE_KEY_<Repo ID>`, all uppercase)
   - Add the *public* key as *writeable* deployment key `github-mirror` to the destination repository
3. **Add configuration** to [`mirror.yml`](./.github/workflows/mirror.yml)
4. **Set default branch** of the destination repository according to upstream

```yml
mirror_config:
    - {
        src_repo: "<Upstream Git URL>",
        dest_repo: "<Destination Repo Name>",
        key_id: "<Repo ID>",
    }
    - ...
```

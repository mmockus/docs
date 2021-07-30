---
sidebar_position: 11
---

# SSH

```bash
ssh-keygen
ssh-copy-id username@remote_host
```

use ssh key `id_rsa` or specify `-i` `~/.ssh/public_key.pub`

Keep `ssh-agent` running.

```bash
eval $(ssh-agent -s)
ssh-add ~/.ssh/my_private_key
```

:::warning
`ssh-agent` does not persist on windows/wsl and must be restarted.
:::

![TODO](https://img.shields.io/badge/TO-DO-blue) <https://www.digitalocean.com/community/questions/how-to-switch-from-password-to-ssh-key-authentication>
Cutover to keybased authentication.

## Overview

## Configuration

## References

<https://www.digitalocean.com/community/tutorials/how-to-configure-ssh-key-based-authentication-on-a-linux-server>
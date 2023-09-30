# Secure Copy (SCP) with ProxyJump

This guide demonstrates how to use `scp` with the `ProxyJump` option to securely copy files through an intermediary server.


## Using ProxyJump with SCP

To copy files from your local machine to server `three` through server `four`, use the following command:

```bash
scp -o 'ProxyJump=four@10.8.0.34' /path/to/local/file three@192.168.1.185:/path/on/server/three/
```

## Simplifying SCP with SSH Config
If you frequently use ProxyJump, you can simplify the process by adding an entry to your `~/.ssh/config` file:

```bash
Host serverthree
    HostName 192.168.1.185
    User three
    ProxyJump four@10.8.0.34
```

With this configuration, you can use scp in a more concise manner:

```bash
scp /path/to/local/file serverthree:/path/on/server/three/
```

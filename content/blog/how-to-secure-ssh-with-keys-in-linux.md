---
title: "How to Secure SSH With Keys in Linux"
date: "2024-01-02T15:12:12+09:00"
draft: false
tags: [Linux, Server, SSH, Security]
cover:
  image: ""
  alt: ""
  caption: ""
---

Using passwords to connect to a server is convenient, but not secure.
Malicious users can try to brute force your password and gain access to your server.
To prevent this, you can use **SSH keys** to connect to your server.
In this post, I will show you how to set up SSH keys on your server with Linux.

# Generating SSH Keys

To generate SSH keys, use the `ssh-keygen` command.
By default, the command generates a Ed25519 key pair, which is more secure than RSA.
You can just press enter to use the default values.
If you want to use a passphrase in addition, you can enter it when prompted.

```bash
ssh-keygen
```

> if you want to generate a RSA key pair, use the `-t rsa` option.

# Where are my SSH keys?

`ssh-keygen` saves the **private key** in `~/.ssh/id_ed25519` and the **public key** in `~/.ssh/id_ed25519.pub`.

> If you generated a RSA key pair, the private key is saved in `~/.ssh/id_rsa` and the public key is saved in `~/.ssh/id_rsa.pub`.

## What are public key and private key?

The **public key** is used to encrypt the data and the **private key** is used to decrypt the data.
So, you can share your public key with anyone without worrying about security.
Contrary to that, you should **never share your private key** with anyone.

# Copying the public key to your server

To add your SSH keys to your server, you need to copy your public key to your server.
You can do this with the `ssh-copy-id` command.
It will copy your public key to your server and add it to the `~/.ssh/authorized_keys` file.

```bash
ssh-copy-id user@server
```

> If you want to copy a specific public key, you can use the `-i` option.
>
> ```bash
> ssh-copy-id -i ~/.ssh/id_ed25519.pub user@server
> ```

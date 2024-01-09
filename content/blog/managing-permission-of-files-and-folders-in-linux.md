---
title: "Managing Permission of Files and Folders in Linux"
date: "2024-01-09T13:52:24+09:00"
draft: false
tags: ["Mogakso", "Linux", "System Administration", "Security"]
cover:
  image: ""
  alt: ""
  caption: ""
---

If you are a Linux user, you might have seen the following message when you try to install a package or run a command.

```bash
$ apt install vim
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
```

This is because you don't have the permission to install a package.
In this post, I will explain how to manage permission of files and folders in Linux.

# Why do we need permission?

Linux is a **multi-user operating system**.
It means that multiple users can use the same computer at the same time.

Let's say that you have a single computer in your house and you share it with your family.
In some cases, you might want to restrict their access to your valuable files.
This is where **permission** comes in.

Permission is a set of **rules** that determines who can access a file or folder.

# Types of permission

There are three types of permission.

1. Read (r)
2. Write (w)
3. Execute (x)

## Permission representation

For example, if the file is read only, it is represented as `r--`.
If the file is readable and writable, it is represented as `rw-`.
If the file is readable, writable, and executable, it is represented as `rwx`.

## Permission representation as numbers

Permission can also be represented as numbers.
Each permission is assigned as a digit in binary.
For example, `rwx` is `111` in binary, which is `7` in decimal.
`rw-` is `110` in binary, which is `6` in decimal.
`r--` is `100` in binary, which is `4` in decimal.

# Managing permission

Permission of a file or folder is managed by **owner**, **group**, and **others**.

## Checking Owner, Group, and Others

To check the owner, group, and others of a file or folder, use `ls -l` command.

```bash
$ ls -l example.txt
-rw-r--r-- 1 tux parents 0 Jan  9 14:00 example.txt
```

In this example, the owner is `tux`, the group is `parents`.

And the permission of the file is `rw-r--r--`.
It looks scary, but it is actually simple.

You can divide the permission into three parts.
`rw-`, `r--`, and `r--`.
The first part is the permission of the **owner**, the second part is the permission of the **group**, and the third part is the permission of **others**.
Therefore, this permission can also be represented as `644`.

## Changing owner

To change the owner of a file or folder, use `chown` command.

```bash
$ chown [owner] [file]
```

## Changing group

To change the group of a file or folder, use `chgrp` command.

```bash
$ chgrp [group] [file]
```

## Changing permission

To change the permission of a file or folder, use `chmod` command.

```bash
$ chmod [permission] [file]
```

For example, if you want to make a file readable, writable, and executable for the owner, readable for the group, and readable for others, you can use `chmod 744 example.txt`.

For easier modification, you can use `+` and `-` to add or remove permission.

```bash
$ chmod u+x example.txt # Add executable permission to the owner
$ chmod g-w example.txt # Remove writable permission from the group
$ chmod o-r example.txt # Remove readable permission from others
```

# Conclusion

In this post, I explained how to manage permission of files and folders in Linux.
If you have any questions or suggestions, please leave a comment below.

> This post is written for **2024 Winter Mogakso**.

# References

> [Linux Basics for Hackers](https://nostarch.com/linuxbasicsforhackers) by OccupyTheWeb, Chapter 5

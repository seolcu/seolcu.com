---
title: "Package Manager Basics in Linux"
date: "2024-01-15T21:46:29+09:00"
draft: false
tags: ["Mogakso", "Linux", "System Administration"]
cover:
  image: ""
  alt: ""
  caption: ""
---

If you are new to Linux, you might be wondering what a **package manager** is.
A package manager is a tool that allows you, update, and remove software on your computer.
It also helps you manage dependencies between different packages.
There are many different package managers available for Linux, but they all have some common features.
In this article, we will discuss the _pure basics_ of package managers in Linux.

# Why do we need a package manager?

You might be wondering why we need a package manager.
The answer is simple: **it makes installing software easier**.

Recall your experience of installing software on Windows.
You had to download the installer from the internet, run it, and then follow the instructions.
If you wanted to uninstall the software, you had to go through the same process again.
This is not very convenient, especially if you want to install multiple programs at once.
Also, this process is prone to viruses and malware if you are downloading software from unknown sources.

With a package manager, you can install software with a single command.
You don't have to worry about downloading the installer from the internet or running it.
The package manager will take care of everything for you.
It will also keep track of all the software installed on your system and allow you to update or remove them easily.
In addition, package managers are more secure than installing software manually.
They only install software from trusted sources and verify that it hasn't been tampered with.

In short, package managers make installing software **easier** and **more secure.**

# What is a package?

A package is a collection of files that make up a software program.
It contains all the files needed to run the program, including executables, libraries, and configuration files.

For example, if you want to install the Firefox web browser on your computer, you would download a package containing all the files needed to run Firefox.
This package would include the Firefox executable, libraries, and configuration files.
When you install the package, all these files will be copied to your computer.
You can then run Firefox by executing the Firefox executable.

# How to use a package manager?

There are many different package managers available for Linux.
It differs from distribution to distribution.
If you are using Debian-based distributions like Ubuntu, you can use the `apt` command to manage packages.
If you are using Red Hat-based distributions like Fedora, you can use the `dnf` command to manage packages.
There are also many other package managers like `pacman` and `zypper`.

In this article, we will use the `apt` command to manage packages.

## Installing packages

To install a package, you can use the `apt install` command.
Since installing packages requires root privileges, you need to use `sudo` before the command.
For example, to install the Firefox web browser, you can run the following command:

```bash
sudo apt install firefox
```

This command will download the Firefox package from the internet and install it on your computer.

## Updating packages

To update a package, you can use the `apt update` command.
What you should know is that this command only updates the **package list**.
So, `apt update` will not upgrade any packages on your system.
To upgrade packages, you need to use the `apt upgrade` command.

In short, `apt update` updates the package list, while `apt upgrade` upgrades packages.
So if you want to update all packages on your system, you need to run both commands:

```bash
sudo apt update && sudo apt upgrade
```

## Removing packages

To remove a package, you can use the `apt remove` command.
For example, to remove the Firefox web browser, you can run the following command:

```bash
sudo apt remove firefox
```

This command will remove the Firefox package from your system.
Note that this command **will not remove any dependencies** installed by the Firefox package.
If you want to remove all dependencies installed by the Firefox package, you need to use the `apt autoremove` command.

```bash
sudo apt autoremove firefox

# or, if you want to remove all unused dependencies
sudo apt autoremove
```

## Searching for packages

To search for a package, you can use the `apt search` command.
In this case, you don't need to use `sudo` because searching for packages doesn't require root privileges.
For example, to search for the Firefox web browser, you can run the following command:

```bash
apt search firefox
```

This command will search for the Firefox package in the package list.

## Listing installed packages

To list all installed packages, you can use the `apt list` command.
In this case, you don't need to use `sudo` because listing installed packages doesn't require root privileges.

```bash
apt list
```

This command will list all installed packages on your system.

# Conclusion

In this article, we have discussed the basics of package managers in Linux.
We have learned what a package manager is, why we need it, and how to use it.
We have also learned how to install, update, remove, search for, and list packages using the `apt` command.

If you have any questions or feedback, please leave a comment below.

> This post was written for the **2024 Winter Mogakso Activity**.

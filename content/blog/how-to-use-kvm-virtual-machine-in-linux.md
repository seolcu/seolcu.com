---
title: "How to Use KVM Virtual Machine in Linux"
date: 2023-12-31T11:33:14+09:00
draft: false
tags: ["Linux", "Virtual Machine", "KVM"]
cover:
  image: "/cover/kvm.png"
  alt: "KVM logo"
  caption: ""
---

If you are a Linux user, you may have encountered a situation where you need to use Windows.
Or, you may want to test another Linux distro without installing it on your computer.
In this case, you can use a **virtual machine**.

# What is a virtual machine?

A virtual machine is a virtual computer that runs on your computer.
It is a software that emulates a computer, and you can install an operating system on it and use it like a real computer.
You can safely make a lot of virtual machines on your computer, and you can delete them whenever you want.

# How can I use a virtual machine?

In Linux, you need two components to use a virtual machine.

- **hypervisor**: An engine of a virtual machine.
- **client**: A program that connects to the hypervisor and uses the virtual machine.

In this article, we will use **KVM** as a hypervisor, and **GNOME Boxes** or **virt-manager** as clients.

# Getting Started

## 1. Enable virtualization in BIOS

Before you enable KVM, you need to enable virtualization in BIOS.
The location of the virtualization option may vary depending on the manufacturer, but it is usually located in the CPU or security section.

- For Intel CPUs, it is called **Intel Virtualization Technology** or **Intel VT**. You should enable it.
- For AMD CPUs, it is called **AMD Virtualization** or **AMD-V**. You should enable it.

## 2. Install a virtual machine client

As KVM is already baked into the Linux kernel, you only need to install a client.

If you are a beginner, I recommend **GNOME Boxes**. It is very easy to setup and use.
If you are an advanced user and planning to use Windows 11, I recommend **virt-manager**. It is a powerful client with many features.

### 2-1. GNOME Boxes

GNOME Boxes is a simple virtual machine client for Linux.
It is very easy to setup and use, but it lacks some features, so it is **not easy to install Windows 11** with GNOME Boxes because of TPM 2.0 and Secure Boot.

You can install it from your package manager. If your distro does not have it, you can install it from [Flathub](https://flathub.org/apps/details/org.gnome.Boxes), but it lacks some features such as USB passthrough.

If you are using Debian-based distro, you can install it with the following command:

```bash
sudo apt install gnome-boxes
```

Done! You can now use GNOME Boxes with KVM.

### 2-2. virt-manager

virt-manager is a powerful virtual machine client for Linux.
It is a bit complicated to setup and use, but it has many features, so you **can install Windows 11** with it.

You can install virt-manager from your package manager.

If you are using Debian-based distro, you can install it with the following command:

```bash
sudo apt install virt-manager
```

Now, you need to enable libvirtd service with the following command:

```bash
sudo systemctl enable --now libvirtd
```

Also, you need to add your user to the libvirt group with the following command:

```bash
sudo usermod -a -G libvirt $(whoami)
```

Finally, for networking, you need to create a virtual network(NAT) and set it to autostart with the following commands:

```bash
sudo virsh net-autostart default
```

> or you can do it graphically in virt-manager -> right click on QEMU/KVM -> connection details -> check autostart

Done! You can now use virt-manager with KVM.

If you have any questions, please leave a comment below.

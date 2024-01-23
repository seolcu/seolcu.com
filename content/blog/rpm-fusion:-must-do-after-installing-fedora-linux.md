---
title: "RPM Fusion: Must-Do After Installing Fedora Linux"
date: "2024-01-23T11:01:55+09:00"
draft: false
tags: ["Fedora", "Linux", "RPM Fusion"]
cover:
  image: ""
  alt: ""
  caption: ""
---

In some cases, you might need to install some proprietary software or drivers on Fedora Linux.
Since Fedora is a free and open-source operating system, it does not include proprietary software by default.
However, you can install them from `RPM Fusion`, a community-driven software repository.

# What is `RPM Fusion`?

`RPM Fusion` is a software repository that provides various packages for Fedora Linux.
It includes packages that are not included in the official Fedora repositories due to legal issues or other reasons, such as Steam, NVIDIA drivers, and multimedia codecs.

# How to enable `RPM Fusion`

You can enable `RPM Fusion` in Fedora Linux by running the following commands:

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf config-manager --enable fedora-cisco-openh264
sudo dnf groupupdate core
```

# Installing multimedia packages from `RPM Fusion`

Some crucial multimedia packages are not included in the official Fedora repositories.
So, you need to install them from `RPM Fusion`.

## Common multimedia packages

You should run the following commands to switch to full ffmpeg and to install multimedia codecs:

```bash
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
sudo dnf groupupdate sound-and-video
sudo dnf install rpmfusion-free-release-tainted
sudo dnf install libdvdcss
sudo dnf install rpmfusion-nonfree-release-tainted
sudo dnf --repo=rpmfusion-nonfree-tainted install "*-firmware"
```

## Hardware accelerated codecs

Hardware accelerated codecs are needed for playing videos smoothly.
**Check your graphics card vendor and run the corresponding command below.**

For Intel graphics cards:

```bash
sudo dnf install intel-media-driver
```

For AMD graphics cards:

```bash
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
sudo dnf swap mesa-va-drivers.i686 mesa-va-drivers-freeworld.i686
sudo dnf swap mesa-vdpau-drivers.i686 mesa-vdpau-drivers-freeworld.i686
```

For NVIDIA graphics cards:

```bash
sudo dnf install nvidia-vaapi-driver
```

# Conclusion

In this article, we have learned how to enable `RPM Fusion` and install multimedia packages from it.
If you have any questions, feel free to leave a comment below.

# References

- [RPM Fusion](https://rpmfusion.org/)
- [RPM Fusion - Multimedia](https://rpmfusion.org/Howto/Multimedia)

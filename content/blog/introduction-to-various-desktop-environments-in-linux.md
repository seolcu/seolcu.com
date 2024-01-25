---
title: "Introduction to Various Desktop Environments in Linux"
date: "2024-01-25T19:13:05+09:00"
draft: false
tags:
  ["Linux", "Desktop Environment", "Window Manager", "Compositor", "Mogakso"]
cover:
  image: "/cover/riced-sway.png"
  alt: "Riced Sway by a deleted user in Reddit"
  caption: "Riced Sway by a deleted user in Reddit"
---

There are various desktop environments available in the Linux ecosystem. Each desktop environment has its unique features, allowing users to choose based on their preferences. In this article, we will introduce various desktop environments and window managers (compositors) in Linux.

# What is a Desktop Environment?

**Desktop Environment (DE)** is a collection of programs that provide a **Graphical User Interface (GUI)** on a computer.

It includes basic programs like file managers, text editors, terminals, as well as visible elements such as panels, notification windows, login screens, and window managers. Here are some representative desktop environments:

## 1. GNOME

> Vanilla GNOME
>
> ![Vanilla GNOME](/de/vanilla-gnome.png)

> [Riced GNOME by IuseGentooAndArchBTW](https://www.reddit.com/r/unixporn/comments/18sylyn/gnome_catppuccin_rice/)
>
> ![Riced GNOME](/de/riced-gnome.png)

| Name  | Display Server | Toolkit |
| ----- | -------------- | ------- |
| GNOME | X11, Wayland   | GTK     |

**GNOME** is one of the most popular desktop environments, widely used as the default desktop for Ubuntu.

**Pros:**

1. Simple and consistent design
2. Smooth animation effects
3. Touchscreen and touchpad gestures
4. Excellent scalability
5. Large community support

**Cons:**

1. Limited customization options
2. Steeper learning curve
3. High resource usage

## 2. KDE Plasma

> Vanilla KDE Plasma
>
> ![Vanilla KDE Plasma](/de/vanilla-kde.png)

> [Riced KDE Plasma by FrostDesigns](https://www.reddit.com/r/unixporn/comments/10pjlen/kde_plasma_my_first_rice_ever/)
>
> ![Riced KDE Plasma](/de/riced-kde.png)

| Name       | Display Server | Toolkit |
| ---------- | -------------- | ------- |
| KDE Plasma | X11, Wayland   | Qt      |

**KDE Plasma** is another widely known desktop environment, often praised for its rich features and easy customization.

**Pros:**

1. Extensive feature set
2. Excellent scalability
3. Diverse customization options
4. Lower resource usage
5. Large community support

**Cons:**

1. Complexity due to numerous features
2. Relatively more bugs

## 3. Xfce

> Vanilla Xfce
>
> ![Vanilla Xfce](/de/vanilla-xfce.png)

> [Riced Xfce by Smart_Main6779](https://www.reddit.com/r/unixporn/comments/11yc4d2/xfce_first_xfce_rice/)
>
> ![Riced Xfce](/de/riced-xfce.png)

| Name | Display Server | Toolkit |
| ---- | -------------- | ------- |
| Xfce | X11            | GTK     |

**Xfce** may be less famous than GNOME and KDE Plasma, but it is known for its lightweight resource usage and simplicity.

**Pros:**

1. Lightweight resource usage
2. Low overhead
3. Very fast performance
4. Easy customization
5. Modular design

**Cons:**

1. Basic default design
2. Lack of Wayland support (in development)
3. Smaller community
4. Absence of dedicated applications

## 4. Cinnamon

> Vanilla Cinnamon
>
> ![Vanilla Cinnamon](/de/vanilla-cinnamon.png)

> [Riced Cinnamon by Chargrills21](https://www.reddit.com/r/unixporn/comments/17xzxmk/my_first_rice_cinnamon_584/)
>
> ![Riced Cinnamon](/de/riced-cinnamon.png)

| Name     | Display Server | Toolkit |
| -------- | -------------- | ------- |
| Cinnamon | X11, Wayland   | GTK     |

**Cinnamon** is a desktop environment built on the GNOME framework, known for its familiar design and user-friendly features. It is the default desktop for Linux Mint.

**Pros:**

1. Familiar design
2. Abundance of features
3. Fast performance
4. Easy customization
5. Large community support

**Cons:**

1. Limited Wayland support
2. Basic default design

## 5. LXQt

> Vanilla LXQt
>
> ![Vanilla LXQt](/de/vanilla-lxqt.png)

> [Riced LXQt by Ball_Point_Hammer](https://www.reddit.com/r/unixporn/comments/114q0qm/lxqt_second_rice_attempt/)
>
> ![Riced LXQt](/de/riced-lxqt.png)

| Name | Display Server | Toolkit |
| ---- | -------------- | ------- |
| LXQt | X11            | Qt      |

**LXQt** is a lightweight desktop environment based on LXDE, historically used as the default desktop for Raspberry Pi OS.

**Pros:**

1. Extremely lightweight resource usage
2. Very fast performance
3. Easy customization
4. Modular design

**Cons:**

1. Limited features
2. Lack of Wayland support
3. Small community
4. Absence of dedicated applications
5. Basic default design

---

# What is a Window Manager?

**Window Manager (WM)** is a program that manages windows on a computer.

The window manager handles the position, size, borders, buttons, etc., of windows. Since it is part of the desktop environment, it is included in the desktop environment.

However, some window managers can be used independently of the desktop environment. These window managers are referred to as **Standalone Window Managers**.

Standalone window managers are known for being **lightweight, fast, and offering extensive customization** compared to desktop environments. However, they are more challenging to use and configure than desktop environments, and some programs may not function correctly.

Here are some representative standalone window managers:

## 1. Sway

> Vanilla Sway
>
> ![Vanilla Sway](/de/vanilla-sway.png)

> [Riced Sway by a deleted user](https://www.reddit.com/r/unixporn/comments/ig4faj/sway_rounded_borders_and_drop_shadows_in_sway/)
>
> ![Riced Sway](/de/riced-sway.png)

| Name | Display Server | WM Type         |
| ---- | -------------- | --------------- |
| Sway | Wayland        | Tiling (Manual) |

**Sway** is a **tiling window manager** based on Wayland. It was created as a replacement for the X11-based i3 window manager and shares a similar usage pattern.

**Pros:**

1. Similar usage to i3
2. Large community support

**Cons:**

1. Manual tiling can be inconvenient for users unfamiliar with the tiling method
2. Due to the nature of Wayland WM, multilingual input may not work correctly

## 2. AwesomeWM

> [Riced AwesomeWM by EmpressNoodle](https://www.reddit.com/r/unixporn/comments/hpakeu/awesome_afternoon_in_a_perfect_world/)
>
> ![Riced AwesomeWM](/de/riced-awesome.png)

| Name    | Display Server | WM Type          |
| ------- | -------------- | ---------------- |
| Awesome | X11            | Tiling (Dynamic) |

**AwesomeWM** is a tiling window manager based on X11. It provides basic functionalities like a status bar and launcher, making it relatively accessible to beginners.

**Pros:**

1. Easy layout changes due to dynamic tiling
2. Provides basic functionalities for beginners

**Cons:**

1. Lack of Wayland support

## 3. DWM

> [Riced DWM by indomieslayer](https://www.reddit.com/r/unixporn/comments/12z9q93/dwm_quite_boring_college_setup/)
>
> ![Riced DWM](/de/riced-dwm.png)

| Name | Display Server      | WM Type          |
| ---- | ------------------- | ---------------- |
| DWM  | X11, (DWL: Wayland) | Tiling (Dynamic) |

**DWM** is a tiling window manager based on X11. It stands out for its speed, low resource usage, and extensive customization options. However, it requires manual compilation and is challenging to configure.

**Pros:**

1. Very fast performance
2. Extremely lightweight resource usage
3. Extensive customization
4. Dynamic tiling for easy layout changes

**Cons:**

1. Challenging configuration and customization
2. Requires programming knowledge
3. Compiling is necessary

## 4. Openbox

> [Riced Openbox by adi1090x](https://www.reddit.com/r/unixporn/comments/nqri3y/openbox_did_someone_say_widgets/)
>
> ![Riced Openbox](/de/riced-openbox.png)

| Name    | Display Server | WM Type  |
| ------- | -------------- | -------- |
| Openbox | X11            | Stacking |

**Openbox** is a stacking window manager based on X11. It is known for its familiar usage and easy customization, but development is no longer active.

**Pros:**

1. Familiar usage
2. Easy customization

**Cons:**

1. No longer actively developed
2. Lack of Wayland support

## 5. Hyprland

> [Riced Hyprland by Yoru83](https://www.reddit.com/r/unixporn/comments/12cs8av/hyprland_just_switched_to_archhyprland_from/)
>
> ![Riced Hyprland](/de/riced-hyprland.png)

| Name     | Display Server | WM Type          |
| -------- | -------------- | ---------------- |
| Hyprland | Wayland        | Tiling (Dynamic) |

**Hyprland** is a Wayland-based tiling window manager that focuses on flashy design and animations, differentiating itself from other lightweight window managers.

**Pros:**

1. Flashy design and animations
2. Touchpad gesture support
3. Plugin support through hyprpm
4. Dynamic tiling for easy layout changes
5. Rapid development
6. Large community support

**Cons:**

1. Wayland WM may have issues with multilingual input
2. Heavier resource usage compared to other standalone window managers
3. Relatively unstable as a new window manager
4. Limited distribution support

# Conclusion

These are just a few examples of the diverse desktop environments and window managers in the Linux world. Explore various options, try them out, and choose the one that best suits your preferences and needs.

> This post was written for the **2024 Winter Mogakso Activity.**

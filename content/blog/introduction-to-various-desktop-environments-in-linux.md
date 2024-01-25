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

There are various desktop environments available in Linux. Each desktop environment has unique features, allowing users to choose based on their preferences. In this post, we will introduce different desktop environments and window managers (compositors) in Linux.

# What is a Desktop Environment?

**Desktop Environment** (DE) is a collection of programs that provide a **Graphical User Interface (GUI)** on a computer.

It includes everything from basic programs like file managers, text editors, and terminals to visible elements such as panels, notification windows, login screens, and window managers. Here are some representative desktop environments:

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

**Advantages:**

1. Simple and unified design
2. Smooth animation effects
3. Smooth touchscreen and touchpad gestures
4. Excellent scalability
5. Large community

**Disadvantages:**

1. Limited features
2. Difficult customization
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

**Advantages:**

1. Wide range of features
2. Excellent scalability
3. Extensive customization options
4. Low resource usage
5. Large community

**Disadvantages:**

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

**Advantages:**

1. Light resource usage
2. Low overhead
3. Very fast speed
4. Easy customization
5. Modular design

**Disadvantages:**

1. Suboptimal default design
2. Lack of Wayland support (in development)
3. Relatively smaller community
4. Absence of its own applications

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

**Advantages:**

1. Familiar design
2. Rich features
3. Fast speed
4. Easy customization
5. Large community

**Disadvantages:**

1. Limited Wayland support
2. Suboptimal default design

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

**Advantages:**

1. Extremely light resource usage
2. Very fast speed
3. Easy customization
4. Modular design

**Disadvantages:**

1. Limited features
2. Lack of Wayland support
3. Small community
4. Absence of its own applications
5. Suboptimal default design

---

# What is a Window Manager?

**Window Manager** (WM) is a program that manages **windows** on a computer.

The window manager handles the position, size, borders, buttons, etc., of windows. Since the window manager is part of the desktop environment, it is included in it. However, some window managers can be used independently of the desktop environment and are called **Standalone Window Managers**.

Standalone window managers are lighter, faster, and offer more extensive customization compared to desktop environments. However, they are more challenging to use and configure, and some programs may not function correctly. Here are some representative standalone window managers:

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

**Advantages:**

1. Similar usage to i3
2. Large community

**Disadvantages:**

1. Inconvenient for users unfamiliar with manual tiling
2. Limited support for multilingual input due to Wayland characteristics

## 2. AwesomeWM

> [Riced AwesomeWM by EmpressNoodle](https://www.reddit.com/r/unixporn/comments/hpakeu/awesome_afternoon_in_a_perfect_world/)
>
> ![Riced AwesomeWM](/de/riced-awesome.png)

| Name    | Display Server | WM Type          |
| ------- | -------------- | ---------------- |
| Awesome | X11            | Tiling (Dynamic) |

**Advantages:**

1. Easily change layouts with dynamic tiling
2. Basic features like status bar and launcher included, making it user-friendly

**Disadvantages:**

1. Lack of Wayland support

## 3. DWM

> [Riced DWM by indomieslayer](https://www.reddit.com/r/unixporn/comments/12z9q93/dwm_quite_boring_college_setup/)
>
> ![Riced DWM](/de/riced-dwm.png)

| Name | Display Server      | WM Type          |
| ---- | ------------------- | ---------------- |
| DWM  | X11, (DWL: Wayland) | Tiling (Dynamic) |

**Advantages:**

1. Very fast speed
2. Extremely light resource usage
3. Extensive customization options
4. Easy layout changes with dynamic tiling

**Disadvantages:**

1. Very challenging configuration and customization
2. Requires programming knowledge
3. Compilation required

## 4. Openbox

> [Riced Openbox by adi1090x](https://www.reddit.com/r/unixporn/comments/nqri3y/openbox_did_someone_say_widgets/)
>
> ![Riced Openbox](/de/riced-openbox.png)

| Name    | Display Server | WM Type  |
| ------- | -------------- | -------- |
| Openbox | X11            | Stacking |

**Advantages:**

1. Familiar usage
2. Easy customization

**Disadvantages:**

1. No longer under active development
2. Lack of Wayland support

## 5. Hyprland

> [Riced Hyprland by Yoru83](https://www.reddit.com/r/unixporn/comments/12cs8av/hyprland_just_switched_to_archhyprland_from/)
>
> ![Riced Hyprland](/de/riced-hyprland.png)

| Name     | Display Server | WM Type          |
| -------- | -------------- | ---------------- |
| Hyprland | Wayland        | Tiling (Dynamic) |

**Advantages:**

1. Stunning design and animations
2. Touchpad gesture support
3. Plugin support through hyprpm
4. Easy layout changes with dynamic tiling
5. Rapid development and large community

**Disadvantages:**

1. Limited multilingual input support due to Wayland
2. Heavier resource usage compared to other standalone window managers
3. Still in the early stages of development
4. Limited distribution support

# Conclusion

There are many more desktop environments and window managers available. It is recommended to try different ones and choose the desktop environment or standalone window manager that best suits your preferences.

> This post was written for the **2024 Winter Mogakso Activity**.

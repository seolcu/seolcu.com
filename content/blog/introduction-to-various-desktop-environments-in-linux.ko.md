---
title: "리눅스의 다양한 데스크톱 환경 소개"
date: "2024-01-25T19:13:05+09:00"
draft: false
tags:
  ["Linux", "Desktop Environment", "Window Manager", "Compositor", "Mogakso"]
cover:
  image: "/cover/riced-sway.png"
  alt: "꾸며진 Sway by a deleted user in Reddit"
  caption: "꾸며진 Sway by a deleted user in Reddit"
---

리눅스에는 다양한 데스크톱 환경이 존재합니다.
각 데스크톱 환경은 모두 다른 특징을 가지고 있기 때문에, 사용자의 취향에 맞게 선택할 수 있습니다.
이번 글에서는 리눅스의 다양한 데스크톱 환경과 윈도우 매니저(컴포지터)들을 소개하겠습니다.

# 데스크톱 환경이 무엇인가요?

**데스크톱 환경**(Desktop Environment, 이하 `DE`)은 컴퓨터에 **그래픽 사용자 인터페이스(GUI)** 를 제공하는 프로그램들의 모음입니다.

파일 관리자, 텍스트 편집기, 터미널 등의 기본적인 프로그램부터 패널, 알림창, 로그인 화면, 창 관리자 등 눈에 보이는 모든 것들이 데스크톱 환경에 포함됩니다.

다음은 대표적인 데스크톱 환경들입니다.

## 1. GNOME

> 순정 GNOME
>
> ![순정 GNOME](/de/vanilla-gnome.png)

> [꾸며진 GNOME by IuseGentooAndArchBTW](https://www.reddit.com/r/unixporn/comments/18sylyn/gnome_catppuccin_rice/)
>
> ![꾸며진 GNOME](/de/riced-gnome.png)

| 이름  | 디스플레이 서버 | 툴킷 |
| ----- | --------------- | ---- |
| GNOME | X11, Wayland    | GTK  |

`GNOME`은 가장 유명한 데스크톱 환경 중 하나입니다.
`Ubuntu`의 기본 데스크톱 환경으로 많은 사람들이 사용하고 있습니다.

**장점:**

1. 심플하고 통일된 디자인
2. 부드러운 애니메이션 효과
3. 부드러운 터치스크린 및 터치패드 제스처
4. 뛰어난 확장성
5. 매우 큰 커뮤니티

**단점:**

1. 부족한 기능
2. 어려운 커스터마이징
3. 큰 리소스 사용량

## 2. KDE Plasma

> 순정 KDE Plasma
>
> ![순정 KDE Plasma](/de/vanilla-kde.png)

> [꾸며진 KDE Plasma by FrostDesigns](https://www.reddit.com/r/unixporn/comments/10pjlen/kde_plasma_my_first_rice_ever/)
>
> ![꾸며진 KDE Plasma](/de/riced-kde.png)

| 이름       | 디스플레이 서버 | 툴킷 |
| ---------- | --------------- | ---- |
| KDE Plasma | X11, Wayland    | Qt   |

`KDE Plasma`는 `GNOME`과 함께 가장 유명한 데스크톱 환경 중 하나입니다.
다양한 기능과 쉬운 커스터마이징으로 유명합니다.

**장점:**

1. 매우 다양한 기능
2. 뛰어난 확장성
3. 매우 다양한 커스터마이징
4. 적은 리소스 사용량
5. 큰 커뮤니티

**단점:**

1. 많은 기능으로 인한 복잡함
2. 상대적으로 많은 버그

## 3. Xfce

> 순정 Xfce
>
> ![순정 Xfce](/de/vanilla-xfce.png)

> [꾸며진 Xfce by Smart_Main6779](https://www.reddit.com/r/unixporn/comments/11yc4d2/xfce_first_xfce_rice/)
>
> ![꾸며진 Xfce](/de/riced-xfce.png)

| 이름 | 디스플레이 서버 | 툴킷 |
| ---- | --------------- | ---- |
| Xfce | X11             | GTK  |

`Xfce`는 `GNOME`과 `KDE Plasma`에 비해 덜 유명하지만, 많은 사람들이 사용하고 있습니다.
`GNOME`과 `KDE Plasma`에 비해 가벼운 리소스 사용량과 적은 부하로 유명합니다.

**장점:**

1. 가벼운 리소스 사용량
2. 적은 부하
3. 매우 빠른 속도
4. 쉬운 커스터마이징
5. 모듈화된 설계

**단점:**

1. 좋지 않은 기본 디자인
2. Wayland 지원 부재 (개발 중)
3. 상대적으로 작은 커뮤니티
4. 자체 애플리케이션 부재

## 4. Cinnamon

> 순정 Cinnamon
>
> ![순정 Cinnamon](/de/vanilla-cinnamon.png)

> [꾸며진 Cinnamon by Chargrills21](https://www.reddit.com/r/unixporn/comments/17xzxmk/my_first_rice_cinnamon_584/)
>
> ![꾸며진 Cinnamon](/de/riced-cinnamon.png)

| 이름     | 디스플레이 서버 | 툴킷 |
| -------- | --------------- | ---- |
| Cinnamon | X11, Wayland    | GTK  |

`Cinnamon`은 `GNOME`을 기반으로 만들어진 데스크톱 환경입니다.
친숙한 디자인으로 사용하기 쉬우면서도 많은 기능을 제공해 `Linux Mint`의 기본 데스크톱 환경으로 많이 사용됩니다.

**장점:**

1. 친숙한 디자인
2. 많은 기능
3. 빠른 속도
4. 쉬운 커스터마이징
5. 큰 커뮤니티

**단점:**

1. 부족한 Wayland 지원
2. 부족한 기본 디자인

## 5. LXQt

> 순정 LXQt
>
> ![순정 LXQt](/de/vanilla-lxqt.png)

> [꾸며진 LXQt by Ball_Point_Hammer](https://www.reddit.com/r/unixporn/comments/114q0qm/lxqt_second_rice_attempt/)
>
> ![꾸며진 LXQt](/de/riced-lxqt.png)

| 이름 | 디스플레이 서버 | 툴킷 |
| ---- | --------------- | ---- |
| LXQt | X11             | Qt   |

`LXQt`는 `LXDE`를 기반으로 만들어진 초경량 데스크톱 환경입니다.
과거 라즈베리파이 OS의 기본 데스크톱 환경으로 많이 사용되었습니다.

**장점:**

1. 매우 가벼운 리소스 사용량
2. 매우 빠른 속도
3. 쉬운 커스터마이징
4. 모듈화된 설계

**단점:**

1. 부족한 기능
2. Wayland 지원 부재
3. 작은 커뮤니티
4. 자체 애플리케이션 부재
5. 좋지 않은 기본 디자인

---

# 윈도우 매니저가 무엇인가요?

**윈도우 매니저**(Window Manager(Compositor), 이하 `WM`)는 **창**을 관리하는 프로그램입니다.

윈도우 매니저는 창의 위치, 크기, 테두리, 버튼 등을 관리합니다.
윈도우 매니저는 데스크톱 환경의 일부분이기 때문에, 데스크톱 환경에 포함되어 있습니다.

그러나, 일부 윈도우 매니저는 데스크톱 환경과 독립적으로 사용될 수 있습니다.
이런 윈도우 매니저를 **독립적 윈도우 매니저(Standalone WM)** 라고 부릅니다.

독립형 윈도우 매니저는 데스크톱 환경에 비해 **더 가볍고 빠르며, 더욱 멋지고 다양한 커스터마이징이 가능합니다.**
하지만, 데스크톱 환경에 비해 사용법과 설정 방법이 훨씬 어렵고, 일부 프로그램들이 제대로 동작하지 않을 수 있습니다.

다음은 대표적인 독립적 윈도우 매니저(Standalone WM) 들입니다.

## 1. Sway

> 순정 Sway
>
> ![순정 Sway](/de/vanilla-sway.png)

> [꾸며진 Sway by a deleted user](https://www.reddit.com/r/unixporn/comments/ig4faj/sway_rounded_borders_and_drop_shadows_in_sway/)
>
> ![꾸며진 Sway](/de/riced-sway.png)

| 이름 | 디스플레이 서버 | WM 타입        |
| ---- | --------------- | -------------- |
| Sway | Wayland         | 타일링(Manual) |

`Sway`는 `Wayland`를 기반으로 만들어진 **타일링 윈도우 매니저**입니다.
X11을 사용하는 `i3`를 대체하기 위해 만들어졌기 때문에, `i3`와 비슷한 사용법을 가지고 있습니다.

> **타일링 윈도우 매니저**는 창을 타일 형태로 배치하여 디스플레이 공간을 효율적으로 사용하는 윈도우 매니저입니다.

**장점:**

1. `i3`와 비슷한 사용법
2. 큰 커뮤니티

**단점:**

1. Manual 타일링 방식을 사용하기 때문에, 타일링 방식에 익숙하지 않은 사용자에게는 오히려 불편할 수 있음
2. Wayland WM 특성상 다국어 입력기가 제대로 동작하지 않을 수 있음

## 2. AwesomeWM

> [꾸며진 AwesomeWM by EmpressNoodle](https://www.reddit.com/r/unixporn/comments/hpakeu/awesome_afternoon_in_a_perfect_world/)
>
> ![꾸며진 AwesomeWM](/de/riced-awesome.png)

| 이름    | 디스플레이 서버 | WM 타입         |
| ------- | --------------- | --------------- |
| Awesome | X11             | 타일링(Dynamic) |

`AwesomeWM`은 `X11`을 기반으로 만들어진 **타일링 윈도우 매니저**입니다.
다른 독립형 윈도우 매니저와 달리 상태바와 런처 등의 기본적인 기능을 함께 제공하기 때문에, 입문자도 상대적으로 쉽게 사용할 수 있습니다.

**장점:**

1. Dynamic 타일링 방식을 사용하기 때문에, 레이아웃을 쉽게 변경할 수 있음
2. 상태바와 런처 등의 기본적인 기능을 함께 제공하기 때문에, 입문자도 쉽게 사용할 수 있음

**단점:**

1. Wayland 지원 부재

## 3. DWM

> [꾸며진 DWM by indomieslayer](https://www.reddit.com/r/unixporn/comments/12z9q93/dwm_quite_boring_college_setup/)
>
> ![꾸며진 DWM](/de/riced-dwm.png)

| 이름 | 디스플레이 서버     | WM 타입         |
| ---- | ------------------- | --------------- |
| DWM  | X11, (DWL: Wayland) | 타일링(Dynamic) |

`DWM`은 `X11`을 기반으로 만들어진 **타일링 윈도우 매니저**입니다.
직접 소스코드를 수정하여 커스터마이징할 수 있기 때문에, 매우 다양한 커스터마이징이 가능한 만큼 설정 방법이 매우 어렵고 컴파일이 필요합니다.

**장점:**

1. 매우 빠른 속도
2. 매우 가벼운 리소스 사용량
3. 매우 다양한 커스터마이징
4. Dynamic 타일링 방식을 사용하기 때문에, 레이아웃을 쉽게 변경할 수 있음

**단점:**

1. 매우 어려운 설정과 커스터마이징
2. 프로그래밍 지식 필요
3. 컴파일 요구

## 4. Openbox

> [꾸며진 Openbox by adi1090x](https://www.reddit.com/r/unixporn/comments/nqri3y/openbox_did_someone_say_widgets/)
>
> ![꾸며진 Openbox](/de/riced-openbox.png)

| 이름    | 디스플레이 서버 | WM 타입 |
| ------- | --------------- | ------- |
| Openbox | X11             | 스태킹  |

`Openbox`는 `X11`을 기반으로 만들어진 **스태킹 윈도우 매니저**입니다.
친숙한 사용법과 쉬운 커스터마이징이 장점이나, 더 이상 개발이 되지 않고 있습니다.

> **스태킹 윈도우 매니저**는 창을 겹쳐서 배치하는, 일반적인 윈도우 매니저입니다.

**장점:**

1. 친숙한 사용법
2. 쉬운 커스터마이징

**단점:**

1. 더 이상 개발이 되지 않고 있음
2. Wayland 지원 부재

## 5. Hyprland

> [꾸며진 Hyprland by Yoru83](https://www.reddit.com/r/unixporn/comments/12cs8av/hyprland_just_switched_to_archhyprland_from/)
>
> ![꾸며진 Hyprland](/de/riced-hyprland.png)

| 이름     | 디스플레이 서버 | WM 타입         |
| -------- | --------------- | --------------- |
| Hyprland | Wayland         | 타일링(Dynamic) |

`Hyprland`는 `Wayland`를 기반으로 만들어진 **타일링 윈도우 매니저**입니다.
가벼움과 실용성을 추구하는 다른 독립형 윈도우 매니저와 달리 화려한 디자인과 애니메이션에 중점을 둔 윈도우 매니저입니다.

**장점:**

1. 화려한 디자인과 애니메이션
2. 터치패드 제스처 지원
3. hyprpm을 통한 플러그인 지원
4. Dynamic 타일링 방식을 사용하기 때문에, 레이아웃을 쉽게 변경할 수 있음
5. 매우 빠른 개발 속도
6. 큰 커뮤니티

**단점:**

1. Wayland WM 특성상 다국어 입력기가 제대로 동작하지 않을 수 있음
2. 다른 독립형 윈도우 매니저에 비해 무거운 리소스 사용량
3. 신규 윈도우 매니저로써 아직 불안정함
4. 지원하는 배포판이 한정적임

# 결론

이 외에도 정말 다양한 데스크톱 환경과 윈도우 매니저가 존재합니다.
다양한 데스크톱 환경과 윈도우 매니저를 직접 사용해보고, 자신에게 맞는 데스크톱 환경 또는 독립형 윈도우 매니저를 선택해보시기 바랍니다.

> 이 게시물은 **2024 동계 모각소 활동**을 위해 작성되었습니다.

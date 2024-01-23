---
title: "RPM Fusion: Fedora Linux 설치 후 반드시 해야 할 것"
date: "2024-01-23T11:01:55+09:00"
draft: false
tags: ["Fedora", "Linux", "RPM Fusion"]
cover:
  image: ""
  alt: ""
  caption: ""
---

일부 경우에는 Fedora Linux에 독점 소프트웨어나 드라이버를 설치해야 할 수 있습니다.
Fedora는 자유 소프트웨어이자 오픈 소스 운영 체제이기 때문에 기본적으로 독점 소프트웨어를 포함하지 않습니다.
그러나 `RPM Fusion`이라는 커뮤니티 주도의 소프트웨어 저장소에서 이를 설치할 수 있습니다.

# `RPM Fusion`이란?

`RPM Fusion`은 Fedora Linux용 다양한 패키지를 제공하는 소프트웨어 저장소입니다.
이는 Steam, NVIDIA 드라이버, 멀티미디어 코덱과 같은 공식 Fedora 저장소에 포함되지 않는 패키지들을 포함하고 있습니다.

# `RPM Fusion` 활성화 방법

Fedora Linux에서 다음 명령어를 실행하여 `RPM Fusion`을 활성화할 수 있습니다:

```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
sudo dnf config-manager --enable fedora-cisco-openh264
sudo dnf groupupdate core
```

# `RPM Fusion`에서 멀티미디어 패키지 설치

일부 중요한 멀티미디어 패키지는 공식 Fedora 저장소에 포함되어 있지 않습니다.
따라서 이를 `RPM Fusion`에서 설치해야 합니다.

## 일반 멀티미디어 패키지

다음 명령어를 실행하여 완전한 ffmpeg로 전환하고 멀티미디어 코덱을 설치합니다:

```bash
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
sudo dnf groupupdate sound-and-video
sudo dnf install rpmfusion-free-release-tainted
sudo dnf install libdvdcss
sudo dnf install rpmfusion-nonfree-release-tainted
sudo dnf --repo=rpmfusion-nonfree-tainted install "*-firmware"
```

## 하드웨어 가속 코덱

비디오를 부드럽게 재생하려면 하드웨어 가속 코덱이 필요합니다.
**그래픽 카드 제조사를 확인하고 해당하는 명령어를 실행하세요.**

인텔 그래픽 카드용:

```bash
sudo dnf install intel-media-driver
```

AMD 그래픽 카드용:

```bash
sudo dnf swap mesa-va-drivers mesa-va-drivers-freeworld
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
sudo dnf swap mesa-va-drivers.i686 mesa-va-drivers-freeworld.i686
sudo dnf swap mesa-vdpau-drivers.i686 mesa-vdpau-drivers-freeworld.i686
```

NVIDIA 그래픽 카드용:

```bash
sudo dnf install nvidia-vaapi-driver
```

# 결론

이 글에서는 `RPM Fusion`을 활성화하고 멀티미디어 패키지를 설치하는 방법을 배웠습니다.
질문이 있으면 아래 댓글을 자유롭게 남겨주세요.

# 참고 자료

- [RPM Fusion](https://rpmfusion.org/)
- [RPM Fusion - Multimedia](https://rpmfusion.org/Howto/Multimedia)

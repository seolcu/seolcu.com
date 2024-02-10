---
title: "파일 열고 닫기 - 리눅스 시스템 프로그래밍"
date: "2024-02-11T00:42:42+09:00"
draft: false
tags: ["Linux", "Linux System Programming", "Mogakso"]
cover:
  image: ""
  alt: ""
  caption: ""
---

# 파일 열기

```c
FILE *fopen(const char *pathname, const char *mode);
```

파라미터

- `pathname`: 파일 경로
- `mode`: 파일 열기 모드

반환값

- 성공 시: 열린 파일 포인터(`stream`)
- 실패 시: `NULL`

## 파일 열기 모드:

| 모드 | 읽기 | 쓰기 | 파일 포지션 | 파일 존재 시           | 파일이 부재 시 |
| ---- | ---- | ---- | ----------- | ---------------------- | -------------- |
| `r`  | O    | X    | 처음        | 성공                   | 실패           |
| `r+` | O    | O    | 처음        | 성공                   | 실패           |
| `w`  | X    | O    | 처음        | 기존 파일 제거 후 생성 | 생성           |
| `w+` | O    | O    | 처음        | 기존 파일 제거 후 생성 | 생성           |
| `a`  | X    | O    | 끝          | 성공                   | 생성           |
| `a+` | O    | O    | 끝          | 성공                   | 생성           |

# 파일 닫기

```c
int fclose(FILE *stream);
```

파라미터

- `stream`: 열린 파일 포인터

반환값

- 성공 시: `0`
- 실패 시: `EOF`

# 기타 배운점

- 리눅스라면 `man` 명령어를 통해 C 라이브러리 함수에 대한 정보를 얻을 수 있다.
- `string.h` 라이브러리의 `memset` 함수를 통해 메모리를 초기화할 수 있다.
- 에러를 출력할 때 `perror` 함수를 사용하면 에러 메시지를 출력할 수 있다.

# 실습 코드

[Github](https://github.com/seolcu/inflearn-lsp/blob/master/file-basic/file_open.c)

> 이 게시물은 **2024 동계 모각소 활동**을 위해 작성되었습니다.

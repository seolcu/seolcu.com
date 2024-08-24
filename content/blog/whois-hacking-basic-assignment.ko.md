---
title: "Whois 정보보안기초 과제 3"
date: "2024-08-24T15:37:01+09:00"
draft: false
tags: ["Security", "Whois", "Hacking", "Assignment", "Pwnable"]
cover:
  image: ""
  alt: ""
  caption: ""
---

# Whois 정보보안기초 과제 3

이번 정보보안기초 과제는 gdb를 이용해 주어진 바이너리를 분석하는 것이다.

![alt text](/whois-basic-assignment-3/image.png)

우선 분석할 바이너리는 GitHub로 공유되었다. Clone 했더니, `tar`로 압축된 파일이 있어 압축 해제해 주었다.

![alt text](/whois-basic-assignment-3/image-1.png)

분석해야하는 바이너리는 `Handray` 폴더 속의 `for`과 `if`이다. `file`로 확인해보면 두 파일 모두 리눅스 32bit 바이너리라는 것을 알 수 있다. 따라서 분석을 위해 KVM상에서 LMDE 6 32bit를 돌려 작업환경을 옮겼다.

## for

![alt text](/whois-basic-assignment-3/image-2.png)

peda로 `for`를 열어보고 `i fu`로 함수 목록을 확인해보았다. `main` 함수부터 분석해 보기로 했다.

### main 구조

![alt text](/whois-basic-assignment-3/image-3.png)

`pd main`으로 보니 위와 같은 결과가 나왔다. 하나하나 분석해보도록 하자.

### main +3 ~ +13

```plaintext
   0x080484a5 <+3>:	sub    esp,0x4
   0x080484a8 <+6>:	mov    DWORD PTR [ebp-0x4],0x0
   0x080484af <+13>:	lea    eax,[ebp-0x4]
```

`+3`에서. esp에서 4를 뺌으로서 4바이트의 빈 공간을 스택에 만든다.

`+6`에서, 만들어진 4바이트의 공간을 `0x0`으로 초기화한다.

그리고 `+13`에서, 그 공간의 주소를 eax에 저장한다.

이 부분을 C언어로 표현하면 아래와 같다.

```C
int var = 0;
```

### main +16 ~ +27

```plaintext
   0x080484b2 <+16>:	push   eax
   0x080484b3 <+17>:	push   0x804856e
   0x080484b8 <+22>:	call   0x8048350 <__isoc99_scanf@plt>
   0x080484bd <+27>:	add    esp,0x8
```

이 부분을 보면, push 후 `scanf`를 호출하고, add로 스택을 정리하는 것을 볼 수 있다.

특히 add에서 8을 더해주기 때문에, 인자들의 크기의 합이 8바이트라는 것을 알 수 있다. 이때, call 전에 push한 값의 크기의 합 또한 8바이트므로, `scanf`의 인자로 `0x804856e`와 `eax`가 들어간다는 사실을 알 수 있다.

그럼 두 인자는 뭘 의미할까?

첫번째 인자인 `0x804856e`는 주소값이다. 해당 주소에 해당하는 값을 문자열로 확인해보면:

![alt text](/whois-basic-assignment-3/image-5.png)

첫번째 인자는 `"%d"`라는 사실을 알 수 있다. 이는 `scanf`의 포맷 스트링이다.

두번째 인자인 eax는 아까 만들어진 4바이트의 공간의 주소이다.

그러니, 이 부분을 C언어로 표현하면 아래와 같다.

```C
scanf("%d", &var);
```

### main +30 ~ +39

```plaintext
   0x080484c0 <+30>:	mov    eax,DWORD PTR [ebp-0x4]
   0x080484c3 <+33>:	push   eax
   0x080484c4 <+34>:	call   0x804846b <func>
   0x080484c9 <+39>:	add    esp,0x4
```

`+30`에서, `eax`에 `var`의 값을 저장한다. `lea`가 아닌 `mov`이기 때문에 `var`의 실제 값이다.

그리고, 다시 push, call, add의 과정이 나타난다. 마찬가지로 add에서 4를 더해주기 때문에, call 전에 push한 eax(`var`의 값)가 `func` 함수의 인자라는 사실을 알 수 있다.

따라서 이를 C언어로 나타내면:

```C
func(var);
```

### func 구조

![alt text](/whois-basic-assignment-3/image-4.png)

`func` 함수에 대해 알아보기 위해 `pd func`를 한 결과이다. `jmp`와 `cmp`, `jle`를 보아 반복문이 있다는 것을 짐작할 수 있다.

### func +0 ~ +1

```plaintext
   0x0804846b <+0>:	push   ebp
   0x0804846c <+1>:	mov    ebp,esp
```

`func` 함수의 프롤로그 부분이다. 이 부분에서 중요한 점은, 이제 `ebp`의 값이 바뀌었다는거다. 근데 그러면, 인수로 넘겨준 `var`의 값에는 이제 어떻게 접근해야 할까?

생각해보면 아까 push로 `var`의 값을 스택의 최상단으로 올렸다. 그러니, 이제 `ebp`를 이용해 `var`의 값에 접근할 수 있다. 현재 스택의 구조는 아래와 같다.

```
[ebp] : ebp
[ebp+4] : ebp의 이전 값 (`func +0`에서 push해줬음)
[ebp+8] : var의 값
```

따라서 이제부터는, **`ebp+8`** 에 있는 값을 이용해, 인수로 넘겨준 `var`의 값에 접근할 수 있다.

_(사실 브레이크포인트를 찍어서 확인해보면 더 쉽게 알 수 있다. 그러나, 실행하지 않고도 바이너리를 분석하는 연습을 하고 싶었다.)_

### func +3 ~ +6

```plaintext
   0x0804846e <+3>:	sub    esp,0x4
   0x08048471 <+6>:	mov    DWORD PTR [ebp-0x4],0x1
```

스택에 4바이트의 공간을 만들고, 그 공간에 `1`을 넣는 부분이다. 이 함수에 `반복문`이 있다고 짐작했으므로, 이 부분이 반복문에 사용되는 변수일 것이라고 생각해볼 수 있다. 따라서, 변수의 이름을 `i`로 지어주도록 하자.

C언어로는:

```C
int i = 1;
```

### func +13, +46 ~ +50

```plaintext
   0x08048478 <+13>:	jmp    0x8048499 <func+46>
```

`jmp`로 `func +46`으로 이동한다.

```plaintext
   0x08048499 <+46>:	cmp    DWORD PTR [ebp-0x4],0x9
   0x0804849d <+50>:	jle    0x804847a <func+15>
```

`cmp`를 이용해 `i`와 `9`를 비교한다. 만약 `i`가 `9`보다 작거나 같다면(**l**ess or **e**qual), `func +15`로 이동한다.

이렇듯, 이는 반복문의 형태를 띄고 있다. 따라서 이를 C언어로 나타내면 아래와 같다.

```C
while (i <= 9) {
  // do something
}
```

### func 반복문 내부: +15 ~ +39

```plaintext
   0x0804847a <+15>:	mov    eax,DWORD PTR [ebp+0x8]
   0x0804847d <+18>:	imul   eax,DWORD PTR [ebp-0x4]
   0x08048481 <+22>:	push   eax
   0x08048482 <+23>:	push   DWORD PTR [ebp-0x4]
   0x08048485 <+26>:	push   DWORD PTR [ebp+0x8]
   0x08048488 <+29>:	push   0x8048560
   0x0804848d <+34>:	call   0x8048330 <printf@plt>
   0x08048492 <+39>:	add    esp,0x10
```

마찬가지로 call 전후로 push와 add가 있다. add를 보면, 0x10 즉 16바이트를 정리한다. 역시, call 전에 push가 네번 되므로 딱 맞아떨어진다.

printf의 인자를 하나하나 해석해보자.

우선 첫번째 인자인 `0x8048560`은 주소값이다. 해당 주소에 해당하는 값을 문자열로 확인해보면:

![alt text](/whois-basic-assignment-3/image-6.png)

첫번째 인자는 `"%d * %d = %d\n"`라는 사실을 알 수 있다.

두번째 인자인 `ebp+0x8`는 앞서 언급한 것처럼, `func`에 인자로 주어졌던 `var`의 값이다.

세번째 인자인 `ebp-0x4`는 `i`의 값이다.

네번째 인자인 `eax`의 값은 `+15`와 `+18`에서 결정된다. `+15`에서 `eax`를 `var`의 값으로 초기화하고, `+18`에서 `i`와 곱해준다. 따라서 네번째 인자는 `var * i`의 값이다.

따라서 이 부분을 C언어로 나타내면 아래와 같다.

```C
printf("%d * %d = %d\n", var, i, var * i);
```

### func 반복문 내부: +42

```plaintext
   0x08048495 <+42>:	add    DWORD PTR [ebp-0x4],0x1
```

func 반복문의 가장 끝부분이다. `i`를 1 증가시킨다.

따라서, 이를 C언어로 나타내면 아래와 같다.

```C
i++;
```

### func +52 ~ +54

```plaintext
   0x0804849f <+52>:	nop
   0x080484a0 <+53>:	leave
   0x080484a1 <+54>:	ret
```

`func` 함수의 에필로그 부분이다. `nop`로 끝나기에 리턴 값이 없는 `void` 함수임을 알 수 있다.

### main +42 ~ +48

```plaintext
   0x080484cc <+42>:	mov    eax,0x0
   0x080484d1 <+47>:	leave
   0x080484d2 <+48>:	ret
```

`main` 함수의 에필로그 부분이다. `eax`에 `0`을 넣고 끝나기에 리턴 값이 `0`인 `int` 함수임을 알 수 있다.

### 전체를 C언어로 표현하면?

```C
#include <stdio.h>

void func(int var) {
  int i = 1;
  while (i <= 9) {
    printf("%d * %d = %d\n", var, i, var * i);
    i++;
  }
}

int main() {
  int var;
  scanf("%d", &var);
  func(var);
  return 0;
}
```

구구단 코드가 나왔다.

### 실제 컴파일에 사용된 코드

```C
#include <stdio.h>

void func(int a){
	for(int i=1;i<10;i++){
		printf("%d * %d = %d\n",a,i,a*i);
	}
}

int main(){

	int a = 0;
	scanf("%d",&a);

	func(a);
	return 0;
}
```

두 코드를 비교해보면, `for`문과 `while`문의 차이 빼고는 거의 동일하다는 것을 알 수 있다.

---

## if

![alt text](/whois-basic-assignment-3/image-7.png)

`for`과 마찬가지로 `i fu`로 함수 목록을 출력했다. `main` 함수부터 분석해보기로 했다.

### main 구조

![alt text](/whois-basic-assignment-3/image-8.png)

`pd main`으로 본 결과이다. `for`과 비슷하니, 설명상의 중복을 줄이기 위해 간략히 표현되는 부분들이 있을 것이다.

### main +3 ~ +6

```plaintext
   0x080484a5 <+3>:	sub    esp,0x4
   0x080484a8 <+6>:	mov    DWORD PTR [ebp-0x4],0x0
```

4바이트의 빈 공간을 만들고, 그 값은 0으로 초기화한다. 이를 C언어로 나타내면 아래와 같다.

```C
int var = 0;
```

### main +13 ~ +23

```plaintext
   0x080484b6 <+13>:	push   0x8048580
   0x080484bb <+18>:	call   0x8048330 <printf@plt>
   0x080484c0 <+23>:	add    esp,0x4
```

`printf` 함수를 호출한다. 인자로 `0x8048580`을 넘겨준다. 해당 주소에 해당하는 값을 문자열로 확인해보면:

![alt text](/whois-basic-assignment-3/image-9.png)

`"점수를 입력하세요 : "`라는 사실을 알 수 있다. 따라서 `var` 변수는 점수를 입력받는 변수인 것 같다.

따라서 이 부분을 C언어로 나타내면 아래와 같다.

```C
printf("점수를 입력하세요 : ");
```

### main +26 ~ +40

```plaintext
   0x080484c3 <+26>:	lea    eax,[ebp-0x4]
   0x080484c6 <+29>:	push   eax
   0x080484c7 <+30>:	push   0x804859d
   0x080484cc <+35>:	call   0x8048350 <__isoc99_scanf@plt>
   0x080484d1 <+40>:	add    esp,0x8
```

`scanf` 함수를 호출한다.

첫번째 인자인 `0x804859d`가 가리키는 문자열은 `"%d"` 이다.

두번째 인자는 `var`의 주소이다.

따라서 이 부분을 C언어로 나타내면 아래와 같다.

```C
scanf("%d", &var);
```

### main +43 ~ +52

```plaintext
   0x080484d4 <+43>:	mov    eax,DWORD PTR [ebp-0x4]
   0x080484d7 <+46>:	push   eax
   0x080484d8 <+47>:	call   0x804846b <func>
   0x080484dd <+52>:	add    esp,0x4
```

`func` 함수에 `var`의 값(점수)을 인자로 넘겨준다.

따라서 이 부분을 C언어로 나타내면 아래와 같다.

```C
func(var);
```

### func 구조

![alt text](/whois-basic-assignment-3/image-10.png)

수많은 `cmp`가 보인다. 특정 조건을 만족하면 `eax`에 리턴값을 저장하고, `+60`으로 이동하여 함수를 종료한다.

### func +0 ~ +1

```plaintext
   0x0804846b <+0>:	push   ebp
   0x0804846c <+1>:	mov    ebp,esp
```

`for` 문제와 마찬가지로, `func` 함수에 주어진 인자인 `var`의 값은 이제 `ebp+0x8`에 있다.

### func +3 ~ +14

```plaintext
   0x0804846e <+3>:	cmp    DWORD PTR [ebp+0x8],0x59
   0x08048472 <+7>:	jle    0x804847b <func+16>
   0x08048474 <+9>:	mov    eax,0x41
   0x08048479 <+14>:	jmp    0x80484a7 <func+60>
```

`var`의 값이 `0x59`(`89`)보다 작거나 같으면 `+16`으로 이동한다. 그렇지 않으면 `eax`에 `0x41`(`'A'`)를 저장하고, `+60`으로 이동해 리턴한다.

C언어로 나타내면 아래와 같다.

```C
if (var <= 89) {
  // 다음 조건
}
else {
  return 'A';
}
```

### 조건 var <= 89 만족 시: func +16 ~ +27

```plaintext
   0x0804847b <+16>:	cmp    DWORD PTR [ebp+0x8],0x4f
   0x0804847f <+20>:	jle    0x8048488 <func+29>
   0x08048481 <+22>:	mov    eax,0x42
   0x08048486 <+27>:	jmp    0x80484a7 <func+60>
```

`var`의 값이 `0x4f`(`79`)보다 작거나 같으면 `+29`으로 이동한다. 그렇지 않으면 `eax`에 `0x42`(`'B'`)를 저장하고, `+60`으로 이동해 리턴한다.

C언어로 나타내면 아래와 같다.

```C
if (var <= 79) {
  // 다음 조건
}
else {
  return 'B';
}
```

### 조건 var <= 79 만족 시: func +29 ~ +40

```plaintext
   0x08048488 <+29>:	cmp    DWORD PTR [ebp+0x8],0x45
   0x0804848c <+33>:	jle    0x8048495 <func+42>
   0x0804848e <+35>:	mov    eax,0x43
   0x08048493 <+40>:	jmp    0x80484a7 <func+60>
```

`var`의 값이 `0x45`(`69`)보다 작거나 같으면 `+42`으로 이동한다. 그렇지 않으면 `eax`에 `0x43`(`'C'`)를 저장하고, `+60`으로 이동해 리턴한다.

C언어로 나타내면 아래와 같다.

```C
if (var <= 69) {
  // 다음 조건
}
else {
  return 'C';
}
```

### 조건 var <= 69 만족 시: func +42 ~ +53

```plaintext
   0x08048495 <+42>:	cmp    DWORD PTR [ebp+0x8],0x3b
   0x08048499 <+46>:	jle    0x80484a2 <func+55>
   0x0804849b <+48>:	mov    eax,0x44
   0x080484a0 <+53>:	jmp    0x80484a7 <func+60>
```

`var`의 값이 `0x3b`(`59`)보다 작거나 같으면 `+55`으로 이동한다. 그렇지 않으면 `eax`에 `0x44`(`'D'`)를 저장하고, `+60`으로 이동해 리턴한다.

C언어로 나타내면 아래와 같다.

```C
if (var <= 59) {
  // 다음 조건
}
else {
  return 'D';
}
```

### 조건 var <= 59 만족 시: func +55

```plaintext
   0x080484a2 <+55>:	mov    eax,0x46
```

지금까지의 조건을 모두 만족하면, `eax`에 `0x46`(`'F'`)을 저장한다.

### func +60 ~ +62

```plaintext
   0x080484a7 <+60>:	pop    ebp
   0x080484a8 <+61>:	ret
```

함수의 에필로그 부분이다. 위의 조건 중 하나에 해당되는 값을 리턴하고 함수를 종료한다.

### main +55

```plaintext
   0x080484e0 <+55>:	movsx  eax,al
```

다시 `main`으로 돌아오자마자 실행되는 부분이다. 사실 이 부분은 무슨 뜻인지 잘 모르겠다. 단편적으로 안 사실은, `al`과 `ah`는 `ax`의 하위 8비트와 상위 8비트를 나타낸다. 그리고 이 `ax`를 확장한 것이 `eax`라는 것이다. 일종의 전처리같기는 하지만 이게 무슨 의미인지 정확히는 모르겠고, 브레이크포인트를 찍어서 확인해보아도 `eax`의 값이 달라지지 않아서 잘 모르겠다. 추후 알게 된다면 글을 수정해야겠다.

### main +58 ~ +69

```plaintext
   0x080484e3 <+58>:	push   eax
   0x080484e4 <+59>:	push   0x80485a0
   0x080484e9 <+64>:	call   0x8048330 <printf@plt>
   0x080484ee <+69>:	add    esp,0x8
```

`printf` 함수를 호출한다. 첫번째 인자인 `0x80485a0`이 가리키는 문자열은 `"%c 등급입니다.\n"` 이다. 두번째 인자인 `eax`는 앞서 `func` 함수에서 리턴한 값이다.

따라서 이 부분을 C언어로 나타내면 아래와 같다.

```C
printf("%c 등급입니다.\n", func(var));
```

### main +72 ~ +78

```plaintext
   0x080484f1 <+72>:	mov    eax,0x0
   0x080484f6 <+77>:	leave
   0x080484f7 <+78>:	ret
```

`main` 함수의 에필로그 부분이다. `eax`에 `0`을 넣고 끝나기에 리턴 값이 `0`인 `int` 함수임을 알 수 있다.

### 전체를 C언어로 표현하면?

```C
#include <stdio.h>

char func(int var) {
  if (var <= 89) {
    if (var <= 79) {
      if (var <= 69) {
        if (var <= 59) {
          return 'F';
        }
        else {
          return 'D';
        }
      }
      else {
        return 'C';
      }
    }
    else {
      return 'B';
    }
  }
  else {
    return 'A';
  }
}

int main() {
  int var;
  printf("점수를 입력하세요 : ");
  scanf("%d", &var);
  printf("%c 등급입니다.\n", func(var));
  return 0;
}
```

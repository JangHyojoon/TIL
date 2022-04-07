# CLI 커맨드



### cd (Change Directory)

* 현재 워킹 디렉토리를 변경할 때 사용
* cd .. 하면 부모 디렉토리로 이동

*.. 부모(상위)디렉토리*

*. 자신(현재) 디렉토리*



## ls 

* 현재 워킹 디렉토리의 폴더/파일 확인
* `ls -a -l` 을 을 활용하면 숨김폴더와 자세한 정보을 확인 가능



## touch

* `touch a.txt`  형식으로 파일을 만듬



## mkdir

* `mkdir 디렉토리이름` 형식으로 폴더 생성

* 만약 폴더 이름(happy hacking)에 공백이 있다면?

  `mkdir happy hacking` 라 명령하면 'happy'와 'hacking' 폴더 두가지가 생성됨

* 폴더 이름에 공백이 있다면 따옴표를 사용해 폴더 이름을 묶어줘야 한다

  `'mkdir happy hacking'`





## 마크다운 문법



### 1. 제목

- #을 사용합니다. 갯수에 따라 중첩이 가능합니다



### 2. 목록

- 순서가 없는 목록은 `- * +` 를 사용
- 순서가 있는 목록은 `1. 2. 3.` 과 같은 숫자를 사용
- `tab 키`를 이용해서 들여쓰기



### 3. 강조

- 글자의 스타일링을 표현합니다.

1. **기울임** : `*글자*` 혹은 `_글자_`
2. **굵게** : `**글자**` 혹은 `__글자__`
3. **취소** : `~~글자~~`



### 4. 코드

- 한 줄 코드인 **인라인 코드**와 여러 줄 코드인 **블록 코드**로 나눌 수 있습니다.

1. 인라인(Inline) 코드 : `inline code`처럼 백틱을 통해 코드를 감싸줍니다.
2. 블록(Block) 코드 : ````python` 처럼 백틱을 3번 입력하고 코드의 종류를 작성합니다.



### 5. 링크

- 클릭하면 해당 주소로 이동할 수 있는 링크를 표현합니다.
- `[표시할 글자](이동할 주소)` 형태로 작성합니다.



### 6. 이미지

- 마크다운 문서에 이미지를 삽입할 수 있습니다.
- `![대체 텍스트](이미지 주소)` 형태로 작성합니다.
- `대체 텍스트`란 이미지를 정상적으로 불러오지 못했을 때 표시되는 문구입니다.
- Typora에서는 이미지 파일을 끌어와서 놓아도 자동 업로드 됩니다.



### 7. 인용

* \> 를 사용합니다. 갯수에 따라 중첩이 가능합니다.



### 8. 표

- `파이프( | )`와 `하이픈( - )`을 이용해서 행과 열을 구분합니다.

- 테이블 양쪽 끝의 `파이프( | )`는 생략 가능합니다.

- 헤더 셀을 구분할 때는 `3개 이상의 하이픈( - )`이 필요합니다.

- Typora에서는 `ctrl + T` 를 통해서 쉽게 표 생성이 가능합니다.

  (Mac은 `option + command + t`)

- 행을 늘릴 때는 `ctrl + enter` 를 누릅니다.



### 9. 수평선

- 구분 선을 생성합니다.
- `- * _` 을 3번 이상 연속으로 작성합니다.



### 10. 마크다운 문법 무시

\

백슬레쉬를 이용



## GIT 기초

### 0. GIT의작동 방식

![Untitled](Day01.assets/Untitled.png)

- `Working Directory (= Working Tree)` : 사용자의 일반적인 작업이 일어나는 곳
- `Staging Area (= Index)` : 커밋을 위한 파일 및 폴더가 추가되는 곳
- `Repository` : staging area에 있던 파일 및 폴더의 변경사항(커밋)을 저장하는 곳
- Git은 **Working Directory → Staging Area → Repository** 의 과정으로 버전 관리를 수행











### 1. 초기 설정

​	최초의 한번만 설정

​	누가 커밋 기록을 남겼는지 확인할 수 있도록 이름과 이메일 설정

```
$ git config --global user.name "이름"
$ git config --global user.email "메일 주소"
```

​	작성자가 올바르게 설정되었는지 확인법

```
$ git config --global -l

또는

$ git config --global --list
```



### 2. 기본명령어

#### 1) git init

- 현재 작업 중인 디렉토리를 Git으로 관리한다는 명령어
- `.git` 이라는 숨김 폴더를 생성하고, 터미널에는 `(master)`라고 표기됩니다.
- Mac OS의 경우 `(master)`가 표기되지 않는데, Terminal 업그레이드를 통해 표기할 수 있습니다.

```
$ git init
Initialized empty Git repository in C:/Users/kyle/git-practice/.git/

kyle@KYLE MINGW64 ~/git-practice (master)

```

```
 **주의 사항**

1. 이미 Git 저장소인 폴더 내에 또 다른 Git 저장소를 만들지 않습니다.(중첩 금지) 
   즉, 터미널에 이미 (master)가 있다면, git init을 절대 입력하면 안됩니다.
   
2. 절대로 홈 디렉토리에서 git init을 하지 않습니다. 터미널의 경로가 `~` 인지 확인합니다.
```



#### 2) git status

- Working Directory와 Staging Area에 있는 파일의 현재 상태를 알려주는 명령어

- 어떤 작업을 시행하기 전에 수시로 status를 확인하면 좋습니다.

- 상태

  1. `Untracked` : Git이 관리하지 않는 파일 (한번도 Staging Area에 올라간 적 없는 파일)

  2. `Tracked`:  : Git이 관리하는 파일

      a.`Unmodified` : 최신 상태

      b.`Modified` : 수정되었지만 아직 Staging Area에는 반영하지 않은 상태

      c.`Staged` : Staging Area에 올라간 상태

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```



#### 3) git add

- Working Directory에 있는 파일을 Staging Area로 올리는 명령어
- Git이 해당 파일을 추적(관리)할 수 있도록 만듭니다.
- `Untracked, Modified → Staged` 로 상태를 변경합니다.

```
$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```



#### 4) git commit

- Staging Area에 올라온 파일의 변경 사항을 하나의 버전(커밋)으로 저장하는 명령어
- `커밋 메세지`는 현재 변경 사항들을 잘 나타낼 수 있도록 `의미` 있게 작성하는 것을 권장합니다.
- 각각의 커밋은 `SHA-1` 알고리즘에 의해 반환 된 고유의 해시 값을 ID로 가집니다.
- `(root-commit)` 은 해당 커밋이 최초의 커밋 일 때만 표시됩니다. 이후 커밋부터는 사라집니다.

```
$ git commit -m "first commit"
[master (root-commit) c02659f] first commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 a.txt
```



#### 5) git log

- 커밋의 내역(`ID, 작성자, 시간, 메세지 등`)을 조회할 수 있는 명령어
- 옵션
  - `--oneline` : 한 줄로 축약해서 보여줍니다.
  - `--graph` : 브랜치와 머지 내역을 그래프로 보여줍니다.
  - `--all` : 현재 브랜치를 포함한 모든 브랜치의 내역을 보여줍니다.
  - `--reverse` : 커밋 내역의 순서를 반대로 보여줍니다. (최신이 가장 아래)
  - `-p` : 파일의 변경 내용도 같이 보여줍니다.
  - `-2` : 원하는 갯수 만큼의 내역을 보여줍니다. (2 말고 임의의 숫자 사용 가능)

```
$ git log
commit 1870222981b4731d14ef91d401c68c0bbb2f6e7d (HEAD -> master)
Author: kyle <kyle123@hphk.kr>
Date:   Thu Dec 9 15:26:46 2021 +0900

    first commit
```

```

💡 **옵션과 인자**

명령어를 사용하면서 `-` 혹은 `--`를 통해 옵션을 사용하는 것을 배웠습니다.
옵션과 더불어서 인자라는 개념도 존재하는데요. 옵션과 인자 무엇이 다를까요?

**옵션**은 명령어의 동작 방식을 지정하는 것입니다. 따라서 **생략 가능**합니다.
단순히 기존 기능보다 부가 적인 기능을 원할 때 사용합니다.
예를 들면 `git log --oneline`은 커밋 내역을 한 줄로 보고 싶을 때 사용합니다.
`oneline` 옵션은 말 그대로 부가 적인 기능이므로, 생략해도 `git log`는 정상 동작 합니다.

**인자**는 명령어의 동작 대상을 지정하는 것입니다. 따라서 **생략이 불가능** 합니다.
예를 들면 `git add` 라고만 작성하면 어떤 파일을 Staging Area에 올릴지 모르게 됩니다.
반드시 `git add a.txt` 와 같이 git add 명령어가 동작할 대상을 지정해야 하는데
이때 `a.txt`와 같은 대상을 인자라고 합니다.

```



#### git 명령어 흐름

![Untitled (1)](Day01.assets/Untitled (1).png)





## Github 기초



### 1. Github -> Repositories에서 repository 생성

### 2. repository의 주소를 복사

### 3. git init을 통해 특정 폴더를 로컬 저장소로 만듬

### 4. git remote add <이름> <주소> 형식으로 작성

​		주소는 너무 기니 추후 사용에 불편하여 이름을 붙여 이름으로 명령어 사용

​		git remote -v로 조회

​		git remote rm <이름> 혹은 git remote remove <이름>으로 삭제

​			**로컬과 원격 저장소의 연결을 끊는 것, 원격 저장소 자체를 삭제하진 않음**

### 5. 원격 저장소에 업로드

​		commit한 후 

​		git push <이름> <브랜치 이름> (브랜치 이름은 master로 설정해둠, 왠지는 모름)

​		git push -u <이름> <브랜치 이름> 옵션을 사용하면 이후에는 git push 라고만 작성해도 push됨.



### README.md

- `README.md`는 원격 저장소의 소개와 설명이 담겨있는 일종의 대문 역할을 합니다.
- 반드시 파일 이름을 `README.md`로 지정해야 Github가 인식할 수 있습니다.

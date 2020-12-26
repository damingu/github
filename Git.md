# Git

>  Git은 분산버전관리시스템(DVCS)이다.
>
> 소스코드의 버전 및 이력(commit)을 관리할 수 있다.



# 준비하기

## Git 설치

윈도우에서 git을 활용하기 위해서 git bash를 설치한다.

git을 활용하기 위해서 GUI 툴인 `source tree`,`github desktop`등을 활용 할 수도 있다.

초기 설치를 완료한 이후에 컴퓨터에 `Author`정보를 입력한다.

```bash
$ git config --global user.name { user name }
$ git config --global user.email {user email }
```

- `{}`는 작성하지 않는다!



# (깜깜하고 어두운 터미널에서 길을 잃지 않기 위한)

### 기초 bash 명령어들

> 터미널에서는 항상 자신의 위치(경로)를 확인하자.

- 현재위치 확인하기

```bash
$ pwd
```

- 현재 위치에 있는 파일 목록보기

  ```	 bash
  $ ls 
  $ ls -a(숨긴 파일 )
  ```

- 위치 이동하기

  ```bash
  $ cd 경로명
  $ cd .. #한 단계 위
  $ cd - #바로 이전경로 
  ```

  

# 로컬 저장소(repository)활용하기

### 1. 저장소 초기화

```bash
$ git init 
```

- `.git` 폴더가 생성되며, 여기에 git 관련된 모든 정보가 저장된다. 
- git bash에 `(master)`라고 표시되는데, 이는 현재 `master` 브랜치에 있다는 뜻이다. 



### 2. add

`working directory`, 즉 작업 공간에서 변경된 사항을 이력으로 저장하기 위해서는 반드시 `staging area`를 거쳐야 한다.

```bash
$ git add markdown.md # 특정 파일 하나 추가하기
$ git add images/ # 특정 폴더 추가하기 
$ git add . # 현재 드렉토리에 있는 파일 및 폴더 전체 추가하기
```

-  `add`전 상태

```bash
$ git status 
on branch master

no commits yet

#트레킹 되고 있지 않는 파일들 
# => commit(이력)에 한 번도 담기지 않은 파일들 
untrached files : 
...
```

- add후 상태 

  ```bash
  $ git status 
  on branch master
  
  no commits yet
  #커밋될 변화사항들
  # => staging area에 있는 파일들의 목록이 보여짐
  
  Changes to be commited :
  ...
  ```

  

### 3. Commit

commit은 이력을 확정짓는 명령어로 해당 시점의 스냅샷을 기록한다.

커밋시에는 반드시 메세지를 작성 해야하며, 메세지는 변경사항을 알 수 있도록 명확하게 작성한다.

```bash 
$ git commit -m "명확하고 프로페셔널한 커밋 메세지"
```

커밋 이후에는 아래의 명령어를 통해 지금까지 작성된 이력을 확인한다.

```bash	
$ git log 
```



## 원격저장소(remote repository)  활용하기

원격 저장소 기능을 제공하는 다양한 서비스 중에 github을 기준으로 설명한다.

### 0. 준비사항

- Github에 repository 생성하기

### 1. 원격 저장소 등록

```bash
$ git remote add origin { github url }
```

- `{}` 중괄호는 입력하지 않습니다!
- 등록된 원격 저장소 목록을 보기 위해서는 아래의 명령어를 활용한다

```bash 
$ git remote -v
```



### 2.`push` -원격 저장소 업로드

```bash
$ git push origin master
```

`origin`이라는 이름으로 설정된 원격저장소에 `master` 브랜치로 업로드 `(push)`

이후 변경사항이 생길 때 마다, `add`=>`commit`=>`push`를 반복하면 된다.

그리고 항상 모든 명령어 이후에 연관된 상태를 확인하자.

`status`,`log`,`remote -v`
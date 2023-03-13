# GitHub

# GitHub

## Git

=======

## Git

 <img src="https://velog.velcdn.com/images%2Fjini_eun%2Fpost%2F43ac40ae-8ffe-4a78-9236-27911962664a%2Fimage.png">
 Git은 형상 관리 도구 중 하나로, 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템이다.

## Github

<img src="https://blog.kakaocdn.net/dn/Kl0e8/btqCzADnGSi/fC7tMdoSp6oGS8L2K429V1/img.png">
깃허브(Github)는 분산 버전 관리 툴인 깃(Git)를 사용하는 프로젝트를 지원하는 웹호스팅 서비스이다.

## Github 사용법

### 알아야할 용어

- Repository: 저장소 / 말 그대로 파일이나 폴더를 저장해두는 저장소이다.
- Commit: 파일을 추가, 변경할 내용을 저장소에 저장하는 작업
- push: 추가, 변경한 내용을 원격 저장소에 업로드하는 작업
<hr/>

### git 초기 설정하기

=======

### 알아야할 용어

- Repository: 저장소 / 말 그대로 파일이나 폴더를 저장해두는 저장소이다.
- Commit: 파일을 추가, 변경할 내용을 저장소에 저장하는 작업
- push: 추가, 변경한 내용을 원격 저장소에 업로드하는 작업

### git 초기 설정하기

```bash
git config --global user.name "사용자 이름"
git config --global user.email "사용자 이메일"
```

Git을 컴퓨터에 설치했다면, 먼저, 사용자 이름과 이메일 주소를 설정해 정보를 입력해 두어야 한다. 아래의 명령어를 이용할 수 있다.

<br/>

### git 명령어

<br/>

현재 상태 확인

```bash
git status
```

전체 로그 확인

```bash
git log
```

git 저장소 생성하기

```bash
git init
```

저장소 복제 및 다운로드

```bash
git clone [https: ~~~~ ]
```

저장소에 코드 추가

```bash
git add
```

커밋에 파일의 변경 사항을 한번에 모두 포함

```bash
git add *
```

커밋 생성

```bash
git commit -m "message"
```

원격 저장소의 변경 내용을 현재 디렉토리로 가져오기

```bash
pull
```

변경 내용을 merge 하기 전에 바뀐 내용 비교

```bash
git diff [브랜치 이름] [다른 브랜치 이름]
```

### git branch 관련 명령어

<br/>
git init을 설정하면 해당 폴더에 .git 이라는 파일이 생성됨

```bash
git init
```

github 주소와 연결

```bash
git remote add origin [github 주소]
```

브랜치 생성

```bash
git branch [브랜치명]
```

브랜치 생성

```bash
git branch [브랜치명]
```

해당 브랜치로 이동

```bash
git checkout [브랜치명]
```

브랜치를 생성하고 해당 브랜치로 바로 이동

```bash
git branch -d [브랜치명]
```

원하는 브랜치로 이동했는지 확인

```bash
git branch
```

모든 브랜치 확인

```bash
git brach -a
```

파일 및 폴더 add

```bash
git add .
```

커밋

```bash
git commit -m "commit message"
```

원하는 브랜치로 push하여 원격 서버에 전송

```bash
git push origin [브랜치명]
```

브랜치 삭제

```bash
git branch -d [브랜치 이름]
```

현재 브랜치에 다른 브랜치 수정사항 병합

```bash
git merge [다른 브랜치 이름]
```

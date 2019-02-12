# GIT 이해

2019.02.12

## 명령어 요약

### 로컬

#### 생성 및 확인

```bash
git init   # 로컬에 git 생성
git status   # 현재 상태 확인
```

#### 저장 관련

```bash
git add .   # 전체 스테이징
git add FILE_NAME   # 특정 파일만 스테이징
git commit   # 스테이징된 파일 저장
```

#### 브랜치 관련

```bash
git branch   # 로컬 브랜치 확인
git branch BRANCH_NAME   # 로컬 브랜치 생성
git chechout BRANCH_NAME   # 브랜치 이동
    # HEAD: 현재 바라보고 있는 브랜치
git checkout -b BRANCH_NAME   # 브랜치 생성 및 HEAD를 생성된 브랜치로 이동
git branch -d BRANCH_NAME   # 브랜치 삭제
```

---

### 원격

#### 원격 연결

```bash
git clone "PATH"   # git 프로젝트 가져오기
git clone "PATH" FOLDER_NAME # 현재폴더 안에 새 폴더를 만든 후 그 폴더에 git 프로젝트 가져오기
```

#### 원격 브런치 관리

```bash
git branch -r   # 원격 브랜치 확인
git push origin BRANCH_NAME   # 로컬 브랜치를 원격에도 만들기
git branch --set-upstream-to origin/BRANCH_NAME   # 브랜치 연동
git push origin --delete BRANCH_NAME   # 원격지 브랜치 삭제
```

## 미리 써두는 출처

- [Git 실습강좌](http://www.jejucodingcamp.com/1.pdf)
- [Pro Git](https://git-scm.com/book/ko/v2)
- [Remote 브랜치 관리](https://trustyoo86.github.io/git/2017/11/28/git-remote-branch-create.html)
- [TMON 개발 블로그: Git Commit & Branch 전략](http://blog.naver.com/PostView.nhn?blogId=tmondev&logNo=220763012361)

## Git 특징

- 스냅샷 사용: 수정한 내역에 대해 전체 스냅샷을 가지고 있음

### Git 의 세가지 단계

![The Three Status](https://git-scm.com/book/en/v2/images/areas.png)
출처 : [Pro Git](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EA%B8%B0%EC%B4%88)

- Staging Area : "Index" 라고도 불림, 커밋할 파일에 대한 정보 저장(임시 스냅샷)
- .git directory : 모든 이력이 저장되는 git 저장소

### Git ID

- git 에서 명령을 할 때마다 난수 생성(SHA1 사용)
- 만들어진 난수를 ID 로 사용
- 앞 7자리를 보통 사용함

### Commit

- 파일 히스토리 저장: 단순한 의미의 파일 저장이 아닌, 변경 이력을 같이 담아야 함
- Atomic commit: 개발 과정을 매우 쪼갠 후 그 부분의 이력을 같이 담아 commit 해야 함
- 만약 개발 중 Commit 을 잊어버렸을 경우 각각의 파일마다 Commit 를 하여 변경 로그를 남겨두는 것이 중요함

### Branch

- 가지 : 작업 흐름에 대한 가지
  - 목적 : 각각의 작업을 효율적으로 관리할 수 있도록 함
- 브랜치를 만드는 여러 전략이 있음
- (주관적인 의견) 협업시에는 Git-Flow / TIL 및 OpenSource에는 Github-Flow 사용

#### Git-Flow

![Git Flow Flowchart](https://nvie.com/img/git-model@2x.png)

#### Github-Flow

![Github-Flow](https://cdn-images-1.medium.com/max/1600/1*iHPPa72N11sBI_JSDEGxEA.png)
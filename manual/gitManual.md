# 1. 처음 생성시 적용법

**1-1. 폴더 생성할 아무곳이나 마우스 우클릭 + Git bash here 클릭**

**1-2. 사용자 전역 등록**
```
git config --global user.name (user name)

git config --global user.email (user email)
```

**1-3. 원격 레포지토리 로컬 저장소로 가져오기**

```
git clone http://github.com/(user name)/(repository name)
```
**(Organization 사용시 user name 대신 Organization이름으로 적으면 됨)**

```
git clone http://github.com/(organization name)/(organization's repository name)
```

**1-4. 코드 순차 입력(생성된 폴더에서 bash를 연 다음 - 해당 폴더에 .git이라는 폴더가 존재하는 폴더**

```
git remote // origin이 뜨면 합격

git add . // 여지껏 한 작업들 전부 한방에 이행
git status // 추가한 작업물 확인용

git commit -m "커밋메세지"
ex) git commit -m "add new files"

git push origin main 
```

**1-5 이후 팀프로젝트 진행시 작업 시작 전, clone한 폴더에서 bash를 연 다음 fetch + merge 시키기**

```
git pull origin main // pull 자체가 fetch 시키고 병합(merge)시킴

```
**원래는 fetch 따로 merge 따로 해야함(이해를 위해 예시 남김)**
```
git fetch origin
git merge origin/main
```

# 2. branch 사용

**2-1 브렌치 생성**
```

repository 안에서 issue를 통해 branch 생성 혹은 bash 에서 git branch (branch 명) 을 통해서 생성 
>>  bash 에서 생성시 repository 에서 생성한 branch의 명과 동일하게 생성하면 편함
 	-> git checkout -b (브랜치명)
```

**2-2 브랜치 사용**
```
git checkout (main 혹은 branch 명)
	>> 이후 add 작업부터 시작 하면 됨

```

**2-3 브렌치에 병합 시키기**
```
git checkout main
git pull
git checkout (branch명)
git merge main -> branch 작업 환경에서 main 작업환경과 병합 시킴을 의미
```

**2-4bash에서 브렌치 삭제**
```
git branch -d (브렌치 명)
```

**※ origin 없이 push / pull**
```
git push -u origin 브랜치명 
이후 
git branch -vv 를 통해 origin 확인
```

# 3. 작업 순서 쉽게 하기
**3-1 작업 환경 맞추기**
### 1)작업할 IDE 환경 폴더 열어두기 
### ※작업폴더 열때 .git을 감싸고 있는 폴더가 아닌 .git과 같은레벨의 폴더가 프로젝트 폴더이다.
### 2) .git 이 보이는 폴더에서 우클릭을 통해 bash 열어두기
### ※ 기본적으로 develop이 되어있을거임 이때 충돌 방지를 위해 작업 시작 전에 git pull 해놓기
```
git pull
```
### 3)작업할 영역의 Github를 열고 branch 먼저 생성
### ※브랜치는 issue를 이용하든 projects를 이용하든 만들면 됨 브랜치 명은 해당 팀에서 정한데로
### 4)이후 나온 git 명령어를 열어둔 bash에 복사 붙여넣기(bash는 ctrl v 가 안되게 때문에 마우스 우클릭 권장 
### ※만약 붙여 넣기가 안된다면 아래의 명령어 사용
```
git fetch origin
git checkout (생성한 branch 명)
```
### 이러면 자동으로 해당 브랜치 명으로 bash 작업영역이 바뀐다. -> 이러면 작업 준비 끝

**3-2 작업 주의사항**
### 작업 영역에서 작업이 끝났다면 업로드 하면 되는데 충돌 방지를 위해 add . 하기 전 가져야하는 습관? 
```
git checkout develop // develop 환경으로 바꾸기
git pull // 혹시 먼저 업로드 되어있는 파일이 존재 할수 있음
git checkout (작업한 branch 명) // 다시 원래 bash 작업 영억으로 돌아우기
git merge develop // pull 해온 develop과 본인이 작업하던 브랜치와 파일 병합
```
### 이후 add , commit , push 하면 됨
### 마지막으로 Github에 돌아가서 PR(Pull Request) 하면됨
### ※PR이 성공했다면 develop에 가서 pull 해놓기! (충돌방지)

### ※ 새로운 작업을 시작하려면 브랜치 생성부터 다시 진행하면 됨
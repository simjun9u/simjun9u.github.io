# simjun9u.github.io

## Github 쓰는 법

### Tool
* Terminal> 메뉴>터미널>NewTerminal

### 초기 설정
* 사용자 정보 설정
 * git config --global user.name "Your Name"
 * git config --global user.email "your_email@example.com"
* Github 연결
 * SSH key 생성> ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
 * GitHub 계정에 SSH Key를 등록
  * cat ~/.ssh/id_rsa.pub 명령으로 공개키 복사
  * Github 설정의 SSH and GPG keys에 추가

### 새 프로젝트
* 새 프로젝트 생성
 * Github에서 New Repository 클릭, Create repository.
 * 로컬에 클론> git clone git@github.com:username/repository.git 또는 git clone https://github.com/user/repo.git 
* 복사
 * 클론> 

### Branch
* 원격저장소 확인> 또는(URL, /user/repository.git) git remote -v
* 브랜치 확인> git branch 또는(원격) git branch -r 또는(URL)
* Branch 전환> git switch 브랜치이름(main) 또는 git checkout 브랜치이름(main)
* Branch 생성> git switch -c 새브랜치이름(__) 또는 git checkout -b 새브랜치이름(Test 또는 Test/241201)
* Branch 복원> git restore src/app.js 또는 git checkout main -- src/app.js

### 1_add(stage) 2_commit, Push  
* 확인
 * 푸쉬 전, 스테이지 전후> git status
* 0저장> Ctrl+S (Git은 변경사항 추적 불가)
* 1스테이지> git add .
 * .은 터미널 기준 현재Dir+하위Dir. 즉 git add file1.txt 가능. git add subdir/ 가능. git add -A 현재디렉토리 아래 모든 추적사항 반영가능. 
* 2커밋> git commit -m "커밋 메시지"
 * 변경확인> git commit --dry-run
 * Diff출력> git commit -v 또는 git commit --verbose 
 * 커밋보완> git commit --amend -m "메시지" 또는(메시지 생략) git commit --amend --no-edit
 * 멀티라인 git commit -m "제목" -m "본문" 가능. -a 옵션 add 포함(add & 바로 커밋)
 * 기타 등등 --author --date
* 3푸쉬> git push origin 로컬브랜치이름:원격브랜치이름
 * 첫푸쉬> git push -u origin 브랜치이름 (설명: 원격저장소 생성 u (= --set-upstream))
 * 그이후> git push
 * 강제> git push -f 또는 git push -f origin 브랜치이름
 * origin = Git 원격저장소(remote repository) 기본 별칭(alias 짧) git remote -v로 긴URL 확인, -u (= --set-upstream)

### 병합
* 현재 작업 중 내용 커밋
 * git add .
 * git commit -m "수정 내용 설명"
* main으로 브랜치전환 후 기존브랜치를 main에 병합
 * git checkout main
 * git merge 브랜치이름
* 마무리
 * git push origin main

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
* Checkout (switch, restore로 분화)
 * Branch 전환> git switch 브랜치이름(main) 또는 git checkout 브랜치이름(main)
 * Branch 생성> git switch -c 새브랜치이름(__) 또는 git checkout -b 새브랜치이름(Test 또는 Test/241201)
 * Branch 복원> git restore 파일(src/app.js) 또는 git checkout 파일(src/app.js)
  * 커밋 후 수정 안한 상태로 복원됨. (스테이징 날리거나, git restore --staged <file>)
  * git checkout(전환/복원) main(참조브랜치 지정가능) -- src/app.js(main의 최신 src/app.js를 terminal 현재 작업 디렉토리로 복원)
  * git checkout <커밋 해시, 특정 커밋의 고유 식별자, 그때의 파일을 현재 작업 디렉토리로 복원> -- src/app.js

### 1_add(stage), 2_commit, 3_push, 0_pull  
* 변경사항 확인 (특히 pull 이후)
 * git status (푸쉬 전, 스테이지 전후에)
 * git log
 * git diff origin/main
* 0저장> Ctrl+S (Git은 변경사항 추적 불가)
* 1스테이지> git add .
 * .은 터미널 기준 현재Dir+하위Dir. 즉 git add file1.txt 가능. git add subdir/ 가능. git add -A 현재디렉토리 아래 모든 추적사항 반영가능. 
* 2커밋> git commit -m "커밋 메시지"
 * 변경확인> git commit --dry-run
 * Diff출력> git commit -v 또는 git commit --verbose 
 * 커밋보완> git commit --amend -m "메시지" 또는(메시지 생략) git commit --amend --no-edit
 * 멀티라인 git commit -m "제목" -m "본문" 가능. -a 옵션 add 포함(add & 바로 커밋)
 * 기타 등등 --author --date
* 3푸쉬> git push origin 로컬브랜치. 즉 git push 원격브랜치 로컬브랜치. 통상 git push origin main
 * 첫푸쉬> git push -u origin 브랜치이름 (설명: 원격저장소 생성 u (= --set-upstream))
 * 그이후> git push
 * 이름이 다르면> git push origin 로컬브랜치이름:원격브랜치이름 또는 삭제 git push origin :브랜치이름
 * 강제> git push -f 또는 git push -f origin 브랜치이름
 * origin = Git 원격저장소(remote repository) 기본 별칭(alias 짧) git remote -v로 긴URL 확인, -u (= --set-upstream)
* 4풀> git pull origin 로컬브랜치. 즉 git pull 원격브랜치 로컬브랜치. 통상 git pull origin main
 * 모두> git pull --all
 * 충돌예방> 1commit 2pull 3push
 * 충돌시> git add <파일이름>, git commit -m "메시지"
 * git pull --rebase origin main (merge 대신 rebase.)
  * 1) 원격브랜치(origin/main) 브랜치의 (타인의) 변경사항을 가져와 적용.
  * 2) 현재 로컬브랜치(main 등)에서 작업한 커밋을 새로 적용.(=이 시점 이후로)
  * 3) 로컬브랜치는 origin/main브랜치 위로 위치이동(= 중간에 병합 커밋 미생성) 커밋 기록 깔끔 (선형적 유지).
 * pull = fetch + merge. fetch는 원격 저장소에서 커밋, 브랜치, 태그 등 변경사항 가져옴. (원격저장소 상태를 로컬에서 추적, Diff 확인.)
  * git fetch origin
  * git branch -r (fetch 후 새브랜치 확인)
  * git log origin/main..main (원격메인과 로컬메인 비교)
  * git diff origin/main main (원격메인과 로컬메인 비교)
  * git merge origin/main (원격main브랜치를 로컬main브랜치(여기생략)에 병합)
   * git checkout main (병합대상 기본브랜치로 이동)
   * git merge 병합할브랜치 (병합할브랜치→ main)
   * 충돌발생시, Git은 해당파일을 수정할 상태로 표시, 사용자가 직접 충돌해결해야. git add <파일 이름>, git commit 처럼.
   * git merge --abort (병합취소)
   
### 병합
* Codespace 또는 로컬에서 병합
 * 현재 작업 중 내용 커밋
  * git add .
  * git commit -m "수정 내용 설명"
 * main으로 브랜치전환 후 기존브랜치를 main에 병합
  * git checkout main
  * git merge 브랜치이름
 * 마무리
  * git push origin main
* GitHub Pull Request(Pull 요청) 사용
 * 일단 푸쉬> git push origin 브랜치명
 * Github의 Pull requests탭 New pull request 클릭
  * Base 브랜치(병합대상 브랜치, 통상 main 브랜치), Compare 브랜치(변경사항 있는 작업한 브랜치) 선택.
  * 변경사항 diff 확인. 제목, 설명, 기타사항 작성 >
 * Create Pull Request 클릭 >
  * 다른 팀원들이 리뷰, 변경사항 승인되면,
 * Merge pull request 클릭 >
  * Base 브랜치(예: main)에 병합, (취향) 기존 임시작업 브랜치 삭제

# simjun9u.github.io

## Github 쓰는 법

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
 * 로컬에 클론> git clone git@github.com:username/repository.git

### Commit, Push

# [유데미] Git으로 만드는 전설의 레시피

> git을 공부하고 자주 쓰이는 명령어를 정리

## 0. github 기본 제공 가이드

### 이미 존재하는 local 레포를 remote 레포로 push할 때

```
1. remote repo 등록
git remote add origin < remote 레포 주소 >

2. 브랜치 명을 master(기본)에서 main 으로 변경 (선택적)
git branch -M main

3. remote 레포의 (origin) main 브랜치에 업로드
git push -u origin main
```

## 1. Git으로 레시피 간단하게 만들기

### push : 원격 저장소에 업로드

```
1.
git push -u origin main

2. remote repo에 새 브랜치를 만들면서 push
git push --set-u origin bibimbap
```

### pull : 원격 저장소에 있는 변경 사항을 내 로컬 저장소와 동기화

```
git pull
```

## 2. Git으로 여러 실험을 진행할 브랜치 만들기

### log

```
1. commit log 확인하기
git log

2. 간략하게 확인
git log --oneline
```

### branch

```
1. 브랜치 만들기
git < 브랜치 이름 >

2. 브랜치로 이동하기
git switch < 브랜치 이름 >
```

### merge : 브랜치 병함

```
1. 합병할 주체인 브랜치로 이동
git switch main

2. merge 실행
git merge

3. bibimbap 브랜치가 main 브랜치로 병합됨 (fast-forward 방식)
```

### pull request : merge를 위한 검증 요청

- remote repo에 새 브랜치를 만들고 push를 하면, pull request 탭에서 새로운 compare가 생긴다
- 코멘트를 달거나 할 수 있고, 코멘트를 확인해야만 merge가 가능하도록 할 수도 있다
- 충분한 검증을 거쳐 main 브랜치에 merge해도 될 것 같으면, merge confirm이 이루어진다.

## 3. git으로 레시피 수정하기

### amend : 커밋 메시지를 변경할 때

```
1. 바로 직전 커밋 메시지 수정하기
git commit --amend

2. 직전 커밋 메시지가 뜨면, i 버튼을 눌러 insert 모드로 진입해서 새로운 내용 추가 가능
3. 추가 후 Esc 입력 -> :wq 입력하여 저장 및 종료
```

### 마크다운 문법으로 이미지 첨부하기

```
![사진_이름](사진url)
이렇게 하면 사진 올리기 가능
```

### reset : 이전 commit으로 되돌리기

```
1. 커밋 기록 확인
git log --oneline

2. 되돌아갈 커밋 번호를 복사해서 reset 명령어 실행
git reset < 커밋 번호 >

3. 변경사항이 스테이징되지 않은 그 커밋상태로 되돌아감
```

### 참고

```
git help reset 이렇게 입력하면 reset에 관한 API 파일이 열림
```

### revert : 이전 commit을 지우기

```
1. 커밋 기록 확인
2. 제거할 커밋 번호 복사해서 revert 명령어 실행
git revert < 커밋 번호 >

3. 변경사항도 제거된다
```

### stash : commit하지 않고 임시 저장할 때

```
1. git add 필요 없음
2. stash 메시지와 함께 stash 명령 실행
git stash push -m "stash 메시지"

3. stash list 확인
git stash list

4. 변경사항 확인 (stash id 복사) ex) stash@{0}
git stash show stash@{0} -p

5. stash는 stack 처럼 최근 내용이 가장 위 stash@{0} 로 온다.

6. apply: stash에서 골라서 적용
git stash apply < stash id >
```

### cherry-pick : 다른 브랜치의 커밋을 가져오기

```
1. 체리픽할 커밋 번호를 확인하고 체리픽 실행
git cherry-pick < 커밋 번호 >
이 때, 머지 컨플릭트 발생 가능 -> 수정후 재진행

2. 머지 컨플릭트로 체리픽이 중단됐다가 해결 후 재진행
git cherry-pick --continue

```

## git 오픈 소스에 기여하기

### fork

- 원본 remote repo를 fork 떠오면 내 remote repo로 가져옴
- 내 remote repo에서 작업 후 원본 remote repo로 PR을 보낼 수 있다
- 이후 fork repo가 생성되면 clone하여 내 local repo로 가져옴

## 참고

### GUI 환경에서 Git 사용하기

- 소스트리

### commit message 양식

Udacity (MOOC 플랫폼) commit message 양식이 유명
- https://udacity.github.io/git-styleguide/

### 깃 브랜칭을 연습하는 웹앱
- https://learngitbranching.js.org/?locale=us

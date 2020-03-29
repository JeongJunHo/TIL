# Git을 쓰며 배우는 것들

## error 해결

### Git pull 시 fatal:refusing to merge unrelated histories를 만났을 때

일단 나의 경우는 원격저장소를 만들어놓고 readme.md 파일을 기본 생성 해 둔 후 따로 작업해둔 폴더에 git remote add를 통해 원격저장소를 추가하는 방식으로 진행을 했었다.

원격저장소를 추가한 후 git add, git commit, git push를 진행하게 되면 다음과 같은 에러를 만나게 된다.

```
error: failed to push some refs to 'https://github.com/JeongJunHo/springboot-scheduled-demo.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

```

로컬 저장소가 최신버전이 아니기 때문에 업데이트가 실패했다. 원격저장소를 처음만들때 같이 만들었던 readme.md를 반영하지 않았기 때문인 것 같다. 그래서 시키는대로 git pull을 수행한 후 다시 시도해달라는 요청을 따라서 git pull을 수행하면 현 주제인 fatal:refusing to merge unrelated histories를 만나게 된다. 관련이 없는 기록을 병합할 수 없다는 치명적 오류라고 한다.

그렇기 때문에 pull을 할때 --allow-unrelated-histories 옵션을 주면 정상적으로 pull을 수행할 수 있게 된다.

--allow-unrelated-histories 옵션은 이미 존재하는 두 프로젝트의 기록을 저장하는 드문상황에 사용된다고 한다. 아마도 현재 나의 저장소 같은 상황을 말하는 것 같다.

위에서 언급한 것처럼 git은 기본적으로 서로 관련 기록이 없는 이질적인 두 프로젝트의 병합을 거부하는데, 이 옵션을 사용하면 허용할 수 있게 된다.

## stash

작업 도중에 브랜치를 변경해야 할 때 현재 로컬 저장소에서 작업 중인 파일을 임시 저장하는 용도로 사용하는 명령어이다.

아직 완료되지 않은 작업을 commit 할 수는 없기 때문에 이런 경우에 사용하면 난처한 상황을 해결할 수 있다.

stash에 저장해 둔 후 브랜치를 바꿔 작업을 수행한 후 다시 원래 브랜치로 돌아와 stash에서 작업 파일을 다시 원상복구할 수 있다.



### 저장방법

```
git stash
또는
git stash save
```

현재 작업 중이던 모든 정보가 stash 리스트에 저장된다.

### stash 확인

```
git stash list
```

stash는 여러번 수행할 수 있기 때문에 인덱스 형태로 리스트를 확인할 수 있고 과거 stash 이력 또한 다시 사용할 수 있다.

### stash 적용

```
 가장 최근의 stash 적용
git stash apply
원하는 stash 적용
git stash apply [stash 이름] ex)git stash apply stash@{1}
```

원하는 stash의 이름은 git stash list에서 확인할 수 있다. 

만약 add 명령어를 통해 staged에 작업물을 올려둔 상태로 stash 했다면 --index 옵션을 줘야 staged 상태까지 완벽히 되돌릴 수 있다.

## stash 삭제

stash는 적용을 해도 리스트에 그대로 stash이력이 남아있기 때문에 더이상 사용하지 않는다면 스택에 남아있는 stash를 지우는 명령을 사용해야 한다.

```
가장 최근 stash 제거
git stash drop
stash 이름으로 제거
git stash drop [stash 이름]
```

### stash 적용+삭제

일회성으로 stash를 사용하고 바로 이력까지 삭제하려면 pop 명령어를 사용하면 된다.

```
git stash pop
```

### 적용해버린 stash를 다시 되돌리기

실수로 잘못된 stash를 적용했을 경우 다시 되돌릴 수 있는 명렁어가 있다.

```
가장 최근의 stash를 사용해 패치를 만들고 반대로 적용
git stash show -p | git apply -R
특정 스태쉬를 다시 되돌려야 할 때
git stash show -p [stash 이름] | git apply -R
```


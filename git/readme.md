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
# nginx

## window에서 nginx 사용하기

nginx는 apache와 함께 대표적인 웹서버이다.

window에서 간단하게 웹서버를 실행해 정적웹페이지를 테스트하는 용도로 윈도우에 설치를 진행해보았다.

설치는 하단의 링크를 통해서 window용 nginx를 다운받는다.

URL : http://nginx.org/en/download.html

설치 후 폴더 내의 **nginx.exe** 파일을 실행하면 nginx가 실행되고 주소창에 **localhost**를 입력해서 접근할 수 있다.

nginx 폴더 내부에 html 폴더가 웹서버의 root 경로이며 주의할 점으로 윈도우에서 nginx를 실행할 때 **파일 경로에 한글이 포함된 경로가 있을 경우 정상적으로 실행되지 않는다.**

테스트하고자 하는 파일들을 html 폴더에 넣은 후 nginx를 재기동해준다.

다음으로 nginx의 명령어들이다.

cmd창을 열고 nginx 폴더로 이동한 후 다음 4가지 명령어를 사용할 수 있다.

```
# 강제 종료
nginx -s stop
# 종료
nginx -s quit
# 재시작
nginx -s reload
# 로그파일 재작성
nginx -s reopen
```


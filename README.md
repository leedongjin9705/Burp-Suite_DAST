# Burp-Suite_DAST

버프스윗 메뉴얼

목차

설치법

설정법

검사법

웹 나이트 설치된 사이트 검사법



설치법

상단 파일을 압축 해제하기

cmd 열기

decoder.jar 실행

java -jar decoder.jar

이후 압축 푼 폴더의 images 폴더 이미지 순서대로 실행




설정법



원하는 사이트만 확인

원하는 URL에 대해서만 확인하고 싶을 때 아래처럼 설정.
위의 박스에 들어있으면 해당 타겟만 검사.
아래 박스의 URL은 무시



이후 아래의 체크박스를 체크해주면

아래처럼 원하는 URL만 확인 가능합니다.



Content discovery 설정
해당 검사는 디렉토리, 파일 등을 자동으로 찾아서 추후 검사의 정확도를 높혀줍니다




때에 따라 다르겠지만, 아래처럼 설정하지 않으면 코드에 따라 무한 루프를 도는 경우가 생겨 작업이 끝나지 않았습니다.

경우에 따라 잘 사용하시길 바랍니다.







검사법

프록시 설정




아래 명령어 cmd에서 실행


Start-Process "chrome.exe" -ArgumentList "--proxy-server=http://127.0.0.1:8080", "--ignore-certificate-errors", "#{테스트 URL}"

위의 명령어 실행시 창이 열리게 됩니다. 웹과 연결을 위한 기타 설정이 필요없지만 1회성 입니다.


3. 로그인하기

e-sample에 경우에는 사용자, 관리자 계정이 있고, 계정마다 메뉴가 다르기에 모든 메뉴에 로그인 1번씩 해서 site map 에 쌓아줍니다.

각 계정 로그인 → 사이트 우클릭 → spider this host



디렉토리 찾기
위의 설정법에서 보면 discovery session status 설정법이 있습니다.
그곳의 Control 메뉴로 가서 실행만 시켜주면 자동으로 작업합니다.
시간이 소요되니 퇴근시 돌리는 걸 추천합니다.
너무 오래걸리거나 Tasks queued가 너무 높아지면 무한 루프에 빠진 것이니 설정을 수정, 추가해서
다시 돌리는 게 맞습니다. 안끝납니다.

검사하기

아래 버튼을 클릭하여 검사합니다.








아래 사진은 검사 전의 사진입니다

검사 결과는 해당 칸에 표시되며 어떤 페이지에 취약점이 있는지 확인이 가능합니다.



검사 결과는 100% 정답은 아니고 추측일 수도 있습니다.



확인하기

페이지 1곳을 눌러봅니다.
이후 Request 버튼 클릭


이후 화면 우클릭 후 Send to Repeater 클릭



Repeater 메뉴로 이동



Go 버튼 클릭
우측에는 어떤식으로 취약점으로 탐지됐는지 나오는 화면입니다.
해석이 조금 어려우므로 gpt에 취약점 여부를 물어보시면 됩니다.







웹 나이트 설치된 사이트 검사법

WebKnight.xml 을 연다.

태그(HTTP_Server_Errors)로 아래의 문장을 찾아서 교체해준다

<HTTP_Server_Errors App='Select' Default='0' Explanation='Block the IP address 
if it generates too many HTTP server errors.' Display='Disabled;Block;
Monitor;Block IP;Monitor IP'>0</HTTP_Server_Errors>

Excluded_IP_Addresses 태그를 검색 후 본인 ip를 추가해준다(화이트리스트)

이후 검사한다

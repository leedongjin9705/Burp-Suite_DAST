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
<img width="944" height="728" alt="1" src="https://github.com/user-attachments/assets/bb53bea6-9bdb-43bd-984b-0fe795edd5f5" />



이후 아래의 체크박스를 체크해주면
<img width="1024" height="628" alt="2" src="https://github.com/user-attachments/assets/39c9b58a-3fa4-499c-8053-884e3445856c" />

아래처럼 원하는 URL만 확인 가능합니다.

<img width="398" height="469" alt="3" src="https://github.com/user-attachments/assets/afdbe009-c25c-4819-85d7-152bc81d35a7" />


Content discovery 설정
해당 검사는 디렉토리, 파일 등을 자동으로 찾아서 추후 검사의 정확도를 높혀줍니다
<img width="724" height="600" alt="4" src="https://github.com/user-attachments/assets/922810eb-72b6-4214-ba93-772004511721" />




때에 따라 다르겠지만, 아래처럼 설정하지 않으면 코드에 따라 무한 루프를 도는 경우가 생겨 작업이 끝나지 않았습니다.

경우에 따라 잘 사용하시길 바랍니다.

<img width="935" height="683" alt="5" src="https://github.com/user-attachments/assets/1d724a5d-45c8-4e8e-859b-2495cda1486e" />






검사법

프록시 설정
<img width="1024" height="479" alt="6" src="https://github.com/user-attachments/assets/cb6e34a2-bb3f-46f2-84cc-a65c6de40eb5" />

<img width="553" height="479" alt="7" src="https://github.com/user-attachments/assets/b300d1f6-000c-4595-bb6a-ba6ddbcc92d7" />



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
<img width="949" height="742" alt="8" src="https://github.com/user-attachments/assets/90448ce5-4f95-4315-acdc-af33bdf4f530" />

검사하기

아래 버튼을 클릭하여 검사합니다.
<img width="648" height="521" alt="9" src="https://github.com/user-attachments/assets/f47da06f-5ba5-4faf-88a6-e6b7c97c0175" />








아래 사진은 검사 전의 사진입니다

검사 결과는 해당 칸에 표시되며 어떤 페이지에 취약점이 있는지 확인이 가능합니다.


<img width="441" height="253" alt="10" src="https://github.com/user-attachments/assets/6c31deed-6dc6-4ddc-8c7e-6e8ad931b17e" />

검사 결과는 100% 정답은 아니고 추측일 수도 있습니다.



확인하기

페이지 1곳을 눌러봅니다.
이후 Request 버튼 클릭

<img width="1024" height="780" alt="11" src="https://github.com/user-attachments/assets/ab82c720-ff30-47ab-82ec-4eff07626cca" />

이후 화면 우클릭 후 Send to Repeater 클릭
<img width="501" height="553" alt="12" src="https://github.com/user-attachments/assets/4650d277-c1ff-4678-b7ce-1cbad3faa467" />



Repeater 메뉴로 이동
<img width="1024" height="785" alt="13" src="https://github.com/user-attachments/assets/e70dfb59-ca37-468b-9106-88e9d597ad3a" />



Go 버튼 클릭
우측에는 어떤식으로 취약점으로 탐지됐는지 나오는 화면입니다.
해석이 조금 어려우므로 gpt에 취약점 여부를 물어보시면 됩니다.

<img width="1024" height="773" alt="14" src="https://github.com/user-attachments/assets/7529db9b-fd33-46b3-ad7d-4e0341d83641" />






웹 나이트 설치된 사이트 검사법

WebKnight.xml 을 연다.

태그(HTTP_Server_Errors)로 아래의 문장을 찾아서 교체해준다

<HTTP_Server_Errors App='Select' Default='0' Explanation='Block the IP address 
if it generates too many HTTP server errors.' Display='Disabled;Block;
Monitor;Block IP;Monitor IP'>0</HTTP_Server_Errors>

Excluded_IP_Addresses 태그를 검색 후 본인 ip를 추가해준다(화이트리스트)

이후 검사한다

# 네번째, OWASP Juice Shop 로그인 인증

취약점은 다양하다 예시로 몇개를 이야기한다면 아래와 같다.

1. "JSON Web Token"을 사용하여 JWT 내부의 다른 값을 변경하거나 "Alg" 필드의 값을 "없음"으로 설정하도록 선택할 수있는 CVE-2015-9235 취약점
2. 알고리즘 RS256(비대칭)을 HS256(대칭)으로 변경하는 CVE-2016-5431/CVE-2016-10555 취약점



아래에는 로그인 실패 시 탐지 된 JWT 통신 데이터이다. 그럼 로그인을 성공해보자.

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>



먼저 로그인을 하기 위해서는 아이디를 만들어야 한다. 아이디를 만드는 과정부터 통신을 본다면 아래 이미지 처럼 url 들이 통신 되는 것을 확인 할 수 있는데&#x20;

192.168.149.128:3000/api/SecurityQuestions/&#x20;

passwordsleakcheck-pa.googleapis.com/v1/leaks:lookupSingle&#x20;

192.168.149.128:3000/api/Users/&#x20;

192.168.149.128:3000/api/SecurityAnswers/&#x20;

passwordsleakcheck-pa.googleapis.com/v1/leaks:lookupSingle&#x20;

192.168.149.128:3000/rest/admin/application-configuration

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>



계정을 생성하면 아래 이미지와 같이 계정 생성과 관련한 통신이 찍히는 것을 확인 했는데&#x20;

/api/users/ 경로로 통신을 하는거 같다.

<figure><img src="../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



로그인을 성공하면 아래 이미지와 같이 token을 생성하는 것을 확인 할 수 있는데

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>



첫번째, 'POST /rest/user/login' 경로에서 email, password 값을 랜덤으로 넣어, 성공하는 방법

두번째, JWT 취약점을 이용하여 토큰 값을 변경하는 방법

JWT 취약점을 이용할려면 RS256과 HS256을 알아야 하기 때문에 여기에서 먼저 DVWA와 같이 첫번째 방법으로 진행해보자

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>


















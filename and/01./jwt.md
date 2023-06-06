# JWT 취약점

JWT의 로그인 인증 방법은 간단하게 이야기 하면 클라이언트(사용자)에서 아이디와 비밀번호를 입력하여 로그인을 진행하면 서버는 secret key를 통해 access token을 발급 하고 클라이언트(사용자)에게 JWT를 전달한다. 로그인이 필요한 API를 호출 할 시에 header에 JWT를 전송하고 서버에서 JWT 서명을 학인 한 다음 secret key로 JWT를 디코드하여 사용자의 정보를 얻는다. 정보가 맞으면 서버는 요청에 정상적으로 응답을 한다.

JWT의 구조는 header, payload, signature의 3가지 구조로 되어있다.&#x20;



먼저 header에서는 JWT에서 검증하는 암호화 알고리즘과 token의 타입 등이 포함되어 있다.

<figure><img src="../../.gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>



payload는 token에 데이터를 포함하여 전송한다.

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>



signature는 header와 payload, 시크릿 키 알고리즘이 필요하고 token을 인코딩 된 환경과 대조할 수 있다.

<figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>












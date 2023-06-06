# 보안 설정

JWT Token Signatures



JWT Token Verification&#x20;

● Header&#x20;

○ alg - only allow specific algorithm(s)&#x20;

○ kid - check if present&#x20;

● Verify signature&#x20;

● Validate payload&#x20;

○ iat - issued before current time&#x20;

○ exp - hasn’t expired&#x20;

○ iss - valid issuer&#x20;

○ aud - valid “audience”&#x20;

○ azp - valid client ID if present

● Validate custom “claims”



<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>






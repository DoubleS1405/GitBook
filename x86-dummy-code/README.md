---
coverY: 0
---

# 👩💻 x86 Dummy Code 최적화 프로젝트

x86 어셈블리 코드에 적용된 Dummy Code를 제거하는 것

난독화가 적용된 바이너리에 대해서 원본 코드로 복구하는 작업은 매우 어렵다. 예를 들어 MOV EAX, EBX 명령어와 MOV ECX,EDX가 있다고 하자. 다음은2개의 코드에 대해서 Dummy Code를 적용한 결과이다.

```
Dummy Code 적용 전
MOV EAX, EBX 
MOV ECX, EDX 

Dummy Code 적용 후
MOV EAX, EBX

// Dummy Code 
MOV ECX, EBX
ADD ECX, 1
SUB ECX, 1
// Dummy Code End

MOV ECX, EDX
```

EFLAG를 무시하면, 결과적으로 Dummy Code 적용 전과 Dummy Code 적용 후의  EAX와   ECX의 값은  동일하다. 그렇다면 다음 2개의 코드들을 보자

```
MOV EAX, EBX
MOV ECX, EBX
MOV ECX, EDX

```

```
MOV EAX, EBX

MOV ECX, 1
ADD ECX, 1
MOV ECX, EDX
```

위의 코드들은 Dummy Code가 전체가 아닌 일부만 제거된 상태이다. 그럼에도 원본 코드를 실행했을 때와 동일한 코드가 생성된다. 2개의.코드 모두 동일한 실행 결과가 나오지만 다른 코드이기 때문에 어떤 코드가 원본 코드인지 알 수 있는 방법이 없다.

따라서 이 프로젝트에서의 접근법은 원본 코드로 복구하는 것이 아니라 Dummy Code가 적용된 어셈블리 코드를 최적화 하는 방법으로 접근한다.

대상 프로텍터는 VMProtector 이다. VMProtector에서 사용하는 Dummy Code의  종류들을 나열하고, 이를 최적화 할 수 있는 방법들을 리스팅하고자 한다.

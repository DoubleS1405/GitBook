---
description: 중간표현 Intermediate Representation
---

# 중간 표현

x86 명령어의 경우 하나의 명령어에 여러가지 연산이 포함되어 있다. 예를 들어, ADD EAX, EBX 명령어의 경우 다음의  연산들을  수행한다.\
&#x20;\
tmp = EAX + EBX \
EFLAG(ZF) = isZero(tmp) \
EFLAG(OF) = isAddOverflow(EAX, EBX)\
EFLAG(CF) = isAddCarry(EAX, EBX)\
EFLAG(AF) = isAdjust(EAX, EBX)\
EFLAG(PF) = isParity(tmp)\
EFLAG(SF) = isSign(tmp)\
EAX = tmp

이처럼 하나의 명령어가 실행될 때 수행되는 연산들에 대한 표현을 중간 표현이라고 한다.

중간 표현을 사용하는 이유 : 하나의 명령어가 실행되면 명령어의 실행 결과에 따라서 영향을 미치는 레지스터 및 메모리들이 2개 이상인 경우가 많다. 따라서 각 레지스터 (EFLAGS 포함)와  메모리에 영향을 미치는 모든 연산들을 표현해야 각 x86 명령어 간의 참조 관계를 정확하게 파악할 수 있다. 최적화하려는 일련의 명령어들 간의 참조 관계를 정확히 파악해야 부작용이 없는 (최적화 전의 코드와 실행 결과가 동일하도록) 최적화가 가능하다.

---
description: 명령어 종류 (작성 중)
---

# 중간 표현 오퍼레이터 (명령)

## Unary Operator (오퍼랜드가 1개인 명령어)

ConstInt32 : 32비트 정수 오퍼랜드를 표현하기 위한 특수한 오퍼레이터 (상수 오퍼랜드를 표현하기 위해서만 사용된다.)



## Binary Operator (오퍼랜드가 2개인 명령어)

Add, Sub, Mul, Div

BitVecVal (value, size)\
size 크기만큼의 bit 를 할당한다. \
ex) EAX(1) = BitVecVal(0x1234,32); // 32 비트 정수인 0x1234를 EAX(1) 변수에 할당한다.

cf) ConstInt32(0x1234) 와 BitVecVal(0x1234,32) 차이\
ConstInt32(0x1234) 명령은 오로지 중간표현의 오퍼랜드로 사용되는 명령이고, BitVecVal(0x1234,32) 명령은 32비트 정수 변수 0x1234를 할당하는 명령어이다.\
\
실제 x86 명령어에 대한 중간 표현 예시\
MOV EAX, 0x1234는 EAX = Const32(0x1234) 가 아니라 EAX = BitVecVal(0x1234,32) 로 표현된다

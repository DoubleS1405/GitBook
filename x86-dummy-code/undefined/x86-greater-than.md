---
description: 실행 순서
---

# x86 -> 중간표현 모듈 설계

1. x86 명령어 디코드
2. CreateIR : 디코드된 x86 명령어에 따른 IR 생성 작업 수행
3.  GetOperand : IR 생성을 위한 오퍼랜드를 regValuePool 또는 memValuePool에서 가져오거나 생성함 GetRegister - x86 레지스터 오퍼랜드에 대한 regValuePool에서 Value를 가져온다.

    ```
     - 저장할 Value가 상수가 아닌 경우
    ```

    GetMemory - 최종 EA Value가 상수인 경우 - 해당 EA에 대한 memValuePool에서 Value를 가져온다. - 해당 EA에 대한 memValuePool이 존재하지 않는 경우 LOAD 명령어 생성 (MemValue.find(EA->Int))

    ```
     - EA Value가 상수가 아닌 경우
         - 저장할 Value가 상수인 경우
         - 저장할 Value가 상수가 아닌 경우
    ```
4. 오퍼랜드를 이용해서 IR을 생성함
5.  SetOperand SaveRegister - 저장할 Value가 상수인 경우

    ```
     - 저장할 Value가 상수가 아닌 경우
    ```

    SaveMemory - 최종 EA Value가 상수인 경우 - 저장할 Value가 상수인 경우 - 저장할 Value가 상수가 아닌 경우 - EA Value가 상수가 아닌 경우 - 저장할 Value가 상수인 경우 - 저장할 Value가 상수가 아닌 경우
6. EFLAGS (RFLAGS) 관련 IR 생성 해당 명령어가 EFLAGS의 플래그 중에서 영향을 미치는 플래그에 대한 IR을 생성한다. 원래는 각 Contidion 별 bit를 설정해야 하지만 현재는 t1= SetAddOF(op1,op2) t1 =SetZF(rst) 명령어와 같이 각 Condition Bit를 설정하는 명령어로 표현한다.

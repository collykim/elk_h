# elk_h

### 주요 수집처의 수집 반복되는 수집 불가 에러를 확인할 수 있는 로직이 없음
-> 주요 수집처의 안정적인 수집이 불가능한 것에 대한 문제 인식

-> 그것을 해결하기 위해 방안 모색

-> 로그를 통해서 수집 불가의 원인을 찾아 낼 수 있음

-> 하지만, 원인을 찾아 내기 위해서는 각각의 agent들의 세부정보를 모두 확인해야 해서 비효율적임

-> 반복되는 수집 불가능 agent들을 찾아서 수집 재실행이 필요 

-> 이러한 비효율적인 작업을 개선하기 위해 고도화가 필요하다고 판단

-> ELK로 로그 분석 실시


## 아키텍처 다이어그램 

![ELK_diagram](https://github.com/user-attachments/assets/723a5896-e0ce-41cf-b1ef-ba3bcdc41bb1)


## 작동 원리

### 데이터 수집
Python을 통해 application 실행 log를 모두 수집하여 csv 파일로 변환


### 데이터 흐름

1. appliaction에서 발생하는 실행 log들을 python을 통해 csv파일로 변환
2. 변환된 csv파일을 logstash를 통해 elasticsearch에 저장
3. kibana로 시각화 및 log 분석

### 결과물
status 컬럼에 success와 failed를 확인
failed된 agent들을 종합하여 재실행

# 1. 읽은 책
   ## 쏙쏙 들어오는 함수형 코딩 / 에릭 노먼드 저 
</br>
  
# 2. 공유하고 싶은 부분
## ch1. 쏙쏙 들어오는 함수형 코딩에 오신 것을 환영합니다.

### - 함수형 프로그래머는 코드를 액션, 계산, 데이터로 구분한다.
* 액션: 호출하는 시점과 횟수에 의존 -> 따라서 부르는 것에 조심해야 함 
* 계산, 데이터 : 호출 시점과 횟수에 의존 x -> 실행 여부에 따라 나뉨 -> 계산은 실행 가능하며 실행 전까지 어떻게 동작할 지 알 수 없다. 데이터는 이벤트에 대한 사실을 기록한 것


액션, 계산, 데이터의 차이와 장단점을 잘 알고 파악하는 것이 중요.

일반적으로 쓰기 쉬운 순서 : (어려움) 액션 < 계산 < 데이터 (쉬움)

### - 함수형 사고?
함수형 사고: 함수형 프로그래미가 문제 해결을 위해서 사용하는 기술과 생각

함수형 프로그래밍에서 가장 중요하다고 생각하는 두 가지 개념 
* 액션, 계산, 데이터 
* [일급 추상] 사용 :(함수에 함수를 넘겨서 더 많은 함수를 재사용하는 것?) 

액션은 시간에 의존하기에 가장 다루기 어렵다. 애겻ㄴ에서 시간에 의존하는 부분을 분리하면 더 다루기 쉽다. 

계산은 시간에 의존하지 않는다. 그만큼 다루기 쉽기에 가능한 코드를 계산으로 바꾸는 것이 좋다. 

데이터는 정적이고 해석이 필요하며, 저장하거나 이해하기 쉽고 전송이 편리함 

</br>

## ch2. 현실에서의 함수형 사고
( 이번 챕터에서는 로봇과 함께 일한는 피자집 예시로 설명 )

### - 파트 1 : 계층형 설계 (변경 가능성에 따른 분류)
자주 바뀌지 않는 것을 아래에, 자주 바뀌는 것을 위에 위치하도록 하는 [계층형 설계] 아키텍쳐 패턴 적용

 ex) 비즈니스 규칙 / 도메인 규칙 / 기술 스택 계층  

### - 파트 2 : 일급 추상
시스템 이해를 위해 [타임라인 다이어그램]을 사용하고, 함수를 인자로 받는 [일급 함수] 적용.

 ex) 여러 로봇이 동시에 일하는 [분산 시스템]을 구현했으나, [타임라인]을 맞추지 않은 분산 시스템은 예측 불가능한 순서로 실행된다.  ->  [고차 동작]으로 [타임라인 커팅]을 구현해서 로봇이 서로 기다릴 수 있도록 해결. 


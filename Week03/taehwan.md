# Chapter 10

## 📚 읽은 내용
- CHAPTER 10
  - **중첩 조건문을 보호 구문으로 바꾸기**
  ```js
    function getPayAmount() {
        let result
        if (isDead) {
            result = deadAmount()
        } else {
            if (isSeparated) {
            result = separatedAmount()
            } else {
            if (isRetired) {
                result = retiredAmount()
            } else {
                result = normalAmount()
            }
            }
        }
    return result
    }
  ```
  👇
  ```js
    function getPayAmount() {
    if (isDead) {
        return deadAmount()
    }
    if (isSeparated) {
        return separatedAmount()
    }
    if (isRetired) {
        return retiredAmount()
    }

    return normalAmount()
    }
  ```
  1. 교체해야 할 조건 중 가장 바깥 것을 선택하여 보호 구문으로 바꾼다
  2. 테스트
  3. 1~2반복
  4. 모든 보호 구문이 같은 결과를 반환한다면 보호 구문들의 조건식을 통합(10.2)한다.

  - **조건부 로직을 다형성으로 바꾸기**
  ```js
    switch (bird.type) {
        case '유럽 제비':
            return '보통이다';
        case '아프리카 제비':
            return (bird.numberOfCoconuts > 2) ? '지쳤다' : '보통이다';
        case '노르웨이 파랑 앵무':
            return (bird.voltage > 100) ? '그을렸다' : '예쁘다 😏';
        default:
            return '알 수 없다';
    }
  ```
  👇
  ```js
    class EuropeanSwallow {
        get plumage() {
            return '보통이다';
        }
    }

    class AfricanSwallow {
        get plumage() {
            return (bird.numberOfCoconuts > 2) ? '지쳤다' : '보통이다';
        }
    }

    class NorwegianBlueParrot {
        get plumage() {
            return (bird.voltage > 100) ? '그을렸다' : '예쁘다 😏';
        }
    }
  ```
  1. 다형성 동작을 표현하는 클래스들이 아직 없다면 만들어준다. 이왕이면 적합한 인스턴스를 알아서 만들어 반환하는 팩터리 함수도 함께 만든다.
  2. 호출하는 코드에서 팩터리 함수를 사용하게 한다
  3. 조건부 로직 함수를 슈퍼클래스로 옮긴다.
  4. 서브클래스 중 하나를 선택한다. 서브클래스에서 슈퍼클래스의 조건부 로직 메서드를 오버라이드한다. 조건부 문장 중 선택된 서브클래스에 해당하는 조건절을 서브클래스 메서드로 복사한 다음 적절히 수정한다.
  5. 같은 방식으로 각 조건절을 해당 서브클래스에서 메서드로 구현한다.
  6. 슈퍼클래스 메서드에는 기본 동작 부분만 남긴다. 혹은 슈퍼클래스가 추상 클래스여야 한다면. 이 메서드를 추상으로 선언하거나 서브클래스에서 처리해야 함을 알리는 에러를 던진다.

  - **특이 케이스 추가하기**
  ```js
    if (aCustomer === "미확인 고객") customerName = '거주자';
  ```
  👇
  ```js
  class UnkownCustomer {
    get name() { return '거주자' }
  }
  ```
  1. 컨테이너에 특이 케이스인지를 검사하는 속성을 추가하고, false를 반환하게 한다.
  2. 특이 케이스 객체를 만든다. 이 객체는 특이 케이스인지를 검사하는 속성만 포함하며, 이 속성은 true를 반환하게 한다.
  3. 클라이언트에서 특이 케이스인지를 검사하는 코드를 함수로 추출, 모든 클라이언트가 값을 직접 비교하는 대신 방금 추출한 함수를 사용하돌고 고친다.
  4. 코드에 새로운 특이 케이스 대상을 추가한다. 함수의 반환 값으로 받거나 변환 함수를 적용하면 된다.
  5. 특이 케이스를 검사하는 함수 본문을 수정하여 특이케이스 객체의 속성을 사용하도록 한다.
  6. 테스트
  7. 여러 함수를 클래스로 묶기나 여러 함수를 변환 함수로 묶기를 적용하여 특이 케이스를 처리하는 공통 동작을 새로운 요소로 옮긴다.
  8. 아직도 특이 케이스 검사 함수를 이용하는 곳이 남아 있다면 검사 함수를 인라인한다.
## 📚 느낀점
- 최근 실제로 배우고 있던 다형성에 대해 좀 더 자세히 알게 되었다.
- 다형성이라는 것에 대해 좀 더 잘 활용할 수 있게 된 거 같아 좋았다 
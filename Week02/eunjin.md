1. 읽은 책

   # 	You Don't Know JS
   
2. 공유하고 싶은 부분
    
   # 1부 시작하기 3.1 이터레이션
   ```js
   TypeError: 'x' is not iterable
   ```
   종종 이런 에러가 날 때가 있다. 이터러블이란 무엇일까? 이터러블에 대해 알려면 우선 이터레이션을 알아야한다.   
   이터레이션은 패턴이다. 이 패턴은 데이터를 일정 단위로 쪼개고, 차례로 순회하며 점진적으로 처리한다. 이터레이터 패턴을 사용하면 참조 데이터인 이터레이터가 정의된다.   
   이 패턴의 핵심은 표준화된 방법을 제공하여 일정하게 반복 작업을 수행한다는 것이다. 이터레이터 패턴은 루프가 끝났다는 종료 신호가 필요한데, 자바스크립트에서는 done이라는 프로퍼티가 true가 되면 순회가 끝났다고 판단한다.   
   자바스크립트는 ES6부터 내장 메소드를 통해 이터레이터 패턴을 구현하는 구체적인 규약이 추가되었다.   

   이터레이터를 자바스크립트에서 사용하는 방법에는 `for` 루프와 `...`가 두가지가 있다. `...`은 대칭 형태인 전개구문 (spread syntax), 나머지 매개변수 (rest parameter)를 이용한다. 이때 전개 구문이 이터레이터를 소비하는 이터레이터 소비자다.

   이터레이터 소비 프로토콜은 순회 가능한 값인 이터러블을 소비하는 기술적인 방법이다.   
   자바스크립트에서는 `Map`, `Set`, `['array']`, `'string'` 같이 기본이 되는 자료구조나 컬렉션을 이터러블로 정의한다.
   이터레이터 소비 프로토콜은 이터러블에서 인스턴스를 만들고 이 인스턴스를 소비한다. 인스턴스를 여러 개 만들기만 하면 하나의 이터러블을 여러번 소비할 수 있다.

   ```js
   // 예시
   var greeting = 'hello'; //
   const chars = [ ...greeting ] // 이터레이터인 문자열을 전개 구문으로 소비하여 순회 가능 [ 'h', 'e', 'l', 'l', 'o' ]
   ```

   순회 가능이 되기위해 객체는 반드시 @@iterator 메서드를 구현해야 한다. 즉 Symbol.iterator를 통해 이용할 수 있는 @@iterator 키가 있는 속성이 있어야 한다.

   ![image](https://github.com/Sellmate-Frontend-Study/mini_seminar/assets/59821075/e67690e7-d942-4aa2-a86e-a426c6add6b2)
   ![image](https://github.com/Sellmate-Frontend-Study/mini_seminar/assets/59821075/8a4bbf85-68de-44e3-a7cf-8042fe143c40)



   - [참고](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Iteration_protocols)
   - [참고](https://poiemaweb.com/es6-iteration-for-of)

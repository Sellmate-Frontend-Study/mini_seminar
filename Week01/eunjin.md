1. 읽은 책

   # 	You Don't Know JS
   
2. 공유하고 싶은 부분

   # 1부 시작하기 3.4 프로토타입
   프로토타입이란? 두 객체를 연결하는 연결 장치 -> 이 때, 연결 장치는 숨겨져 있어 보이지 않음. 객체가 생성될 때 만들어지고, 이 장치를 통해 새롭게 생성된 객체는 기존에 존재하는 다른 객체(*)에 연결된다.

   예시를 보면
   ```js
   // 새로 만들어진 homework 객체는 Object.prototype 이라는 다른 객체에 연결되어있다.
   // 이는 생성될 때 연결이 되며 homework 객체는 Object.prototype의 메서드들을 사용할 수 있다.
   var homework = {
      topic: 'JS',
   };
   ```

   객체 프로토타입 연결 장치를 직접 정의하고 싶을 때 Object.create()를 사용해 만들 수 있다.

   ```js
   var otherHomework = Object.create(homework);
   otherHomework.topic; // 'JS'
   ```

   만약 otherHomework의 값을 변경하면 기존 homework 객체의 값은 바뀔까? 정답은 바뀌지 않는다. 이다.
   이유는 homework에 있는 topic은 otherHomework의 topic에 가려지기 때문이다.
   

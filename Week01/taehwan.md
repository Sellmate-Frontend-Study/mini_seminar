# Chapter 10

## 📚 읽은 내용
- CHAPTER 10
  - **조건문 분해하기**
  ```js
  if (!aDate.isBefore(plan.summerStart) && !aDate.isAfter(plan.summerEnd))
    charge = quantity * plan.summerRate;
  else
    charge = quantity * plan.regularRate + plan.regularServiceCharge
  ```
  👇
  ```js
  if (summer())
    charge = summerCharge();
  else
    charge = regularCharge()
  ```
  1. 조건식과 그 조건식에 딸린 조건적을 각각 함수로 추출

  - **조건식 통합하기**
  ```js
  if (anEmployee.seniority < 2) return 0;
  if (anEmployee.monthsDisabled > 12) return 0;
  if (anEmployee.isPartTime) return 0;
  ```
  👇
  ```js
  if (isNotEligibleForDisablity()) return 0;

  function isNotEligibleForDisablity() {
    return ((anEmployee.seniority < 2) || (anEmployee.monthsDisabled > 12) || (anEmployee.isPartTime)));
  }
  ```
  1. 해당 조건식들 모두에 부수효과가 없는지 확인
  2. 조건문 두 개를 선택하여 두 조건문의 조건식들을 논리 연산자로 결합
  3. 테스트
  4. 조건이 하나만 남을 때까지 2~3 과정 반복
  5. 하나로 합쳐진 조건식을 함수로 추출할지 고려
## 📚 느낀점
- 최근 개발하며 가장 필요했던 부분인 조건문 로직을 간소화 시키는 내용이라 인상깊게 보았다.
- 최근 리팩토링을 진행하며 수정했던 방법이 꽤 맞았어서 좋았다 🤟
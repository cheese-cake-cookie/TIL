[문제링크](https://programmers.co.kr/learn/courses/30/lessons/42748)

정렬 카테고리에 속한 문제.

### 풀이

```javascript
function solution(array, commands) {
  return commands.reduce((acc, cur) => {
    acc.push(array.slice(cur[0] - 1, cur[1]).sort((a, b) => a - b)[cur[2] - 1]);
    return acc;
  }, []);
}
```

- n번째를 n번째 index와 착각하지 말 것.
- sort 사용 시 compareFunction을 명시하지 않으면 `유니코드` 순서를 기준으로 정렬하게 된다. 즉 문자로 비교했을 때 "80"은 "9" 보다 앞에 오는 경우도 존재한다는 것이다.

```javascript
function solution(array, commands) {
  return commands.reduce((acc, cur) => {
    const [startPosition, endPosition, position] = cur;
    acc.push(
      array.slice(startPosition - 1, endPosition).sort((a, b) => a - b)[
        position - 1
      ]
    );
    return acc;
  }, []);
}
```

- 다른 사람의 코드를 보고 느낀 부분인데 정답 여부가 달라지는 것은 아니지만 index값을 가지고 직접 대입하는 것 보다는 구조분해할당 문법으로 각 변수의 역할을 명시해주는 편이 가독성 측면에서 좋다고 느꼈다.

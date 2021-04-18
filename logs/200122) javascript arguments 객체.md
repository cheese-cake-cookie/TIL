# javascript arguments 객체

함수에 전달된 인수에 해당하는 `Array 형태`의 객체이다.

- 배열 형태로 반환되지만 엄밀히 말하면 배열의 형태를 띄고 있을 뿐 배열은 아니다.
- 그렇기 때문에 `Array`의 `forEach`, `map` 과 같은 내장 메서드는 갖고 있지 않다.

(반환되는 배열은 arguments 객체의 인스턴스임)

```javascript
const sum = function () {
  let args = arguments,
      sum = 0;
  
  for (let i = 0; i < args.length; i +=1 ) {
    sum += args[i];
  }
  
  return sum;
}

console.log(sum(1, 2, 3, 4, 5)); // 15
```

위 예시와 같이 함수 정의 시 파라미터를 정의하지 않아도 `arguments` 객체를 통해 접근 가능하다.

PHP의 경우 `func_num_args()` 메서드를 통해 함수의 인자를 가져올 수 있다.

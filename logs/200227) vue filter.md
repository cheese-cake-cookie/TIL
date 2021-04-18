filter 는 텍스트 형식을 정형화 할 때 사용한다.

### 사용방법
`filter` property에 filter 정의, filter를 사용할 곳의 표현식 마지막에 파이프 심볼(|) 과 함께 추가한다. 
(filter는 체이닝 가능, 두개 이상의 인자를 받는 것도 가능하다)

```javascript
filter: {
  number: function (value) {
    // 숫자에 3자리 단위로, 를 붙여줌.
    return String(value).replace(/(\d)(?=(\d\d\d)+(?!\d))/g, '$1,');
  }
},
template: `<span>가격: {{ price | number }}</span>`
```

### computed와 무엇이 다른가?
computed는 특정 데이터를 가공 후 return 하기 때문에 동일한 역할을 하더라도 필요로 하는 데이터만큼 property를 선언해 주어야 한다. 

만약 조회수, 가격, 좋아요 수 등등 모든 숫자에 콤마를 붙이고 싶은 경우 computed를 사용하면 각각 콤마를 적용한 조회수, 가격, 좋아요를 대신할 proptery가 필요하다. 
하지만 필터의 경우 다른 데이터라도 동일한 가공이 가능하기 때문에 computed와 용도를 명확히 하여 사용하는게 좋다.

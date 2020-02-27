컴포넌트의 v-model 디렉티브는 컴포넌트 내부 props 디렉티브의 `value` property로 전달된다.

```javascript
<ui-component v-model="{type: placeholder}"></ui-component>

var UIComponent = {
  props: ['value', 'autoLoad'],
  // 이하 생략
}

// 혹은 다음과 같이 기본 타입 지정도 가능하다
var UIComponent = {
  props: {
    value: {
      type: Object,
      default: {}
    },
    autoLoad: {
      type: Boolean,
      default: false
    }
  },
  // 이하 생략
}
```

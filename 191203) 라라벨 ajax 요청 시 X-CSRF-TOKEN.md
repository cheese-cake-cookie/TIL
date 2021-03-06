# 라라벨 ajax 요청 시 X-CSRF-TOKEN

라라벨에서 ajax로 POST, PUT과 같이 정보 갱신이 일어나는 요청을 보내는 경우 CSRF(Cross Site Request Forgery) 공격에 대비하기 위해
'X-CSRF-TOKEN' 정보를 header에 담아 함께 전송해야 한다.

`X-CSRF-TOKEN` 값은 name 요소의 값으로 'csrf-token'을 갖는 meta 태그의 content 요소의 값이다.

즉 다음과 같은 형태로 담겨 있으며

`<meta name="csrf-token" content="{ csrf-token 값 }">`

`document.querySelector('meta[name="csrf-token"]').getAttribute('content')` 과 같이 token 값을 얻어올 수 있다.

#### 참고

* ajax 요청 시 header로 선언하는 값 중 앞에 `X-` 가 붙는 값은 커스텀(사용자 정의) 헤더이며 표준이 아니라는 것을 의미한다.

* POST 요청 시 setRequestHeader 메소드로 콘텐츠 타입(ex: `xhttp.setRequestHeader('Content-type', 'application/json')`)과 
전송방식(ex: `xhttp.setRequestHeader('X-Requested-with', 'XMLHttpRequest')`); 명명 할 것
(이는 ajax를 통한 요청이든, curl을 통한 요청이든 동일하다.)

* ajax 요청 시 크롬 개발자 도구 네트워크 탭을 살펴보면 `options` 요청이 함께 전송되는 것을 볼 수 있다. 
options 요청은 서버가 어떤 메소드를 허용하는지 확인하기 위한 테스트 요청에 해당한다.

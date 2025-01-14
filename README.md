## To do list

- 투두리스트 구현
- json-server를 활용해서 로컬에 REST API 구축 및 연동
- 기본적인 데이터 처리인 생성, 읽기, 수정, 삭제(CRUD)를 구현

### strict mode

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Strict_mode

- 엄격하게 문법 검사를 실시하여 기존에는 무시되던 오류를 발생시킴

### json-server

https://github.com/typicode/json-server

- 짧은 시간에 REST API를 구축해주는 패키지
- 실제 프로덕션에서는 사용하지 않음
- npm을 통해 설치 가능
- 안정버전 설치 권장 !!

#### 라이브 서버와 충돌

라이브 서버와 충돌 그리고 json-server의 안정버전 미설치로 json-server의 자동증분을 이용 못하게 되는 경우가 있었는데, 기존 json-server 삭제, 안정버전 설치 후 라이브서버에 아래 코드를 추가해 해결할 수 있었습니다 !

**.vscode/settings.json**

라이브 서버가 현재 todo list를 증가시킬 때 충돌이 있는 것으로..

```json
{
  "liveServer.settings.ignoreFiles": ["**/*.json", "*.json"]
}
```

<br>

### DOMContentLoaded

https://developer.mozilla.org/ko/docs/Web/API/Window/DOMContentLoaded_event

- 초기 HTML 문서를 완전히 불러오고 분석했을 때 발생

```
window.addEventListener('DOMContentLoaded', (event) => {
    console.log('DOM fully loaded and parsed');
});
```

### Javascript fetch API

https://developer.mozilla.org/ko/docs/Web/API/Fetch_API

- AJAX 요청을 하기 위한 기술
- AJAX란 서버에서 추가 정보를 비동기적으로 가져올 수 있게 해주는 포괄적인 기술을 나타내는 용어
- XHR, JQuery, Fetch 등의 선택지가 있지만 이번 강의에서는 최신 기술인 fetch API를 사용

#### fetch API 사용법

https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch

- fetch api의 response는 실제 json 이 아니다.
- 따라서 fetch api에서는 추가 메서드를 호출해 응답 본문을 받을 필요가 있다. (`.json()`)
  - axios는 이 과정을 자동으로 해주기 떄문에 바로 response를 받을 수 있다.
- body 데이터 타입은 헤더의 content-type 헤더와 일치해야 한다.

```
var url = 'https://example.com/profile';
var data = {username: 'example'};

fetch(url, {
  method: 'POST', // or 'PUT'
  body: JSON.stringify(data), // data can be `string` or {object}!
  headers:{
    'Content-Type': 'application/json'
  }
}).then(res => res.json())
.then(response => console.log('Success:', JSON.stringify(response)))
.catch(error => console.error('Error:', error));

```

### HTML data

https://developer.mozilla.org/ko/docs/Learn/HTML/Howto/Use_data_attributes

- custom attribute를 만들 때 사용
- 표준이 아닌 속성이나 추가적인 DOM 속성

#### javascript에서 접근하기

- dataset 객체를 통해 data 속성을 가져오기 위해서는 속성 이름의 data- 뒷 부분을 사용
- 대시들은 camelCase로 변환되는 것에 주의

```
var article = document.getElementById('electriccars');

article.dataset.columns // "3"
article.dataset.indexNumber // "12314"
article.dataset.parent // "cars"
```

#### javascript로 할당하기

```
var article = document.getElementById('electriccars');

article.dataset.columns = 3
article.dataset.indexNumber = "12314"
```

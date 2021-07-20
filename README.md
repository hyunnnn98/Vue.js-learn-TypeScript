# vue.js-typescript-todo

## Todo ( 할 일 관리 앱 CRUD )
- [x] 할 일 추가
- [x] 할 일 조회
- [x] 할 일 삭제
- [x] 할 일 수정

## Vue 문법
- `v-bind` 속성은 뷰 인스턴스의 데이터 속성을 해당 HTML 요소에 연결할 때 사용한다.
- `v-on` 속성은 해당 HTML 요소의 이벤트를 뷰 인스턴스의 로직과 연결할 때 사용한다.
- 사용자 이벤트에 의해 실행된 뷰 메서드(methods) 함수의 첫 번째 인자에는 해당 이벤트(event)가 들어온다.

```
HTML 입력 요소의 종류에 따라 `v-model` 속성이 각각 다음과 같이 구성된다.
(1) input 태그에는 `value / input`
(2) checkbox 태그에는 `checked / change`
(3) select 태그에는 `value / change`
```

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
